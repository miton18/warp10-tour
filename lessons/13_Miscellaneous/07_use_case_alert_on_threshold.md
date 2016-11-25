# Build an alert **TimeSerie**

This is a use-case, you can adapt the script to your needs.

We start with a server monitoring with alerts detection. 
In this example, the server push metrics about CPU use.
We purpose that a CPU use between 0 and 1 is OK, higher is a problem.

## We need buckets

Fetch a **TimeSerie**, can return lots of points, to do some process it's useful.
But display 50 000 points in a browser is not an easy thing.

So we use `BUCKETIZE` function over our serie. 
Just choose how many points you want to display (the 5th argument of function).

Now you can see an interesting grph of CPU use.

## Get all alerts instance with a THRESHOLDTEST

`THRESHOLDTEST` scan a **TimeSerie** and search for higher values than given parameter.
Call this function on the original **TimeSerie** for an exact result.

In some case, we can considere the CPU use is a problem if it's over used during a defined duration.
If you look for something like that, 
you can use buckets to considere your duration and apply `THRESHOLDTEST` 
on bucketized **TimeSerie**.

We go back with a list of Timestamps.

## Do what you want with alerts

`FOREACH` function take a list (the previous list of Timestamps) and a **Macro**.
So we define a macro, to do something with the value.

In this example, we add a point in a new **TimeSerie** called `alerts`.
The value of the point is a concatenation of 'alert at' and the correspondinf point datas.

`ATTICK` function is used to get point attributes for a specific Timestamp.


last line id here to display the bucketized GTS.

~~~
NOW 'now' STORE
// Create a GTS for a cpu usage metric on a host : 10 000 points
NEWGTS 'os.cpu' RENAME 1 10000 <% 200 * $now + NaN NaN NaN RAND ADDVALUE %> FOR
2000 200 * $now + 100 + NaN NaN NaN 1.1 ADDVALUE
6000 200 * $now + 100 + NaN NaN NaN 1.2 ADDVALUE
'cpuGTS' STORE

[ $cpuGTS bucketizer.max 0 0 100 ] BUCKETIZE 'cpuGTSB' STORE 
// max is empiric solution, prefer mean

// Create a new TimeSeries only for alerts
NEWGTS 'alerts' RENAME 'alertGTS' STORE $alertGTS
// set a limit to trigger the alert
$cpuGTS  1.0 THRESHOLDTEST 
// Define alert macro
<% 
    'ts' STORE 
    $ts NaN NaN NaN 'alert at' $cpuGTS $ts ATTICK ' ' 2 JOIN ADDVALUE 
%> FOREACH

// diplay initial TimeSerie
$cpuGTSB