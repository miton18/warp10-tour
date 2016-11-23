# Filter Framework

The FILTER framework is useful to **select some specific GTS from a set of GTS**. You'll learn to use it with an example: select only the series corresponding to the fuel type "gas oil" using Filter.


## Format
```
[ [GTS] ... [GTS] [labels] filter ] FILTER
```

## Parameters
>`[GTS]`  
> One or several lists of geo time series

>`[labels] `  
> list of label names to use for partitioning the input geo time series. If this list is empty, then all labels will be used.

>`filter`  
> filter function to apply.

## Example

We will use the the FILTER framework to **get from our set of GTS, only the one corresponding to the "gas oil" fuel type**. To do it, **use the function filter.bylabels.**

## Solution

```
// Wrap of the set of GTS
'["60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFsB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wm6sg7.........EjXkB1er4kPwN0WPw6bmY25_VAvnvyUtrFvItgHoC1kyqsnezoMrogUKztyEW69GuRGuZnhPxtDn32ktywfDv643dRykiQ4VFr341UDM7GuqsA4pv_gmMR6mAN7.MGt.2zGfFBu.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aca.0Wb6sg7.........EjXkB1er4kPwN0WPw3b8zvSMmvQUu_uuAtDd6dXF3E2vfjCfDYo41WhzqMyjf7ILmk8ekBeXW077emiMOi8lrBMtUPKVHr3dFurjYJRWacj9kad0k1zQa7jBV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLPXN.54VUXkV.........yyA.k9fRM0flV54fkLTQd6jtCyozzEqwnMMWuNZ02FqvvnPnIc6HxWy_tiwfDv348Zu7GiWnbhf7db9ML6q3nHEC6TIH.EvIZrVP.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Vk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.55FUXkV.........yyA.k9fRM0flV54fkTU9BBPL.jjE3F88jdRyIF_cPCWxhtbKzjD_YmhzEwyS1DLYokWp0NijRxZL39iEg6ZnFL.LdjYjtnbSnhD7CsRwSy1X.PNLBaom.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_sa.0W86sg7.........EjXkB1er4kPwN0WPw6bbVDGevIgjofCrpSqNgj3V7P5rMTQLP_CIs6Hx_ySdnPmeSm__IqZoV0DvPwo1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFsB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wp6sg7.........EjXkB1er4kPwN0WPw6bmY25_VAvAzEr_OrNNYZ_c94WxxpaKjijJa10XK.yDVpMxqLAONG.ZWx1MourwxG5C_nu18hrKlxcRna5y4TFeHdrXIUb0CWWOAjY9tShkTAfMDYm.6k4tpRu.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.56NUXkV.........yyA.k9fRM0flV54fkJz5qkaqYyozU4ntyr_DxwH.WcQSSthOoTZdJCfycxIwULJbhW0LtnmpZJr_AePsJCvoMjzv12uMQR6XuplkzcT6vih3eWsXt7r0.CBRX2u1vX2VAr8d.3YUok01.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Vk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.563UXkV.........yyA.k9fRM0flV54fkTU9BBPL.jgE8vONGVVZIF_cPCWxhtbKzgE6_QyUtrGEWEAGPNHuhlBnXYNckEZUdTQj9nil0ORykiNxS4wbJjJFFzkY_qr0sihRl8i2rzqZoV..YJkxBV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLK1N.54cUXkV.........yyA.k9fRM0flV54fkLTCWmZUjhhz1MnS9fRYP3d.FwEiiwqgx_z9IamlY01N1DLYokWpwzT0KD8HGmgPNQxYdvbrgGMJBWR.GcHXLlc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_7a.0W96sg7.........EjXkB1er4kPwN0WPw6bQehnYlIhjwnUKrOXXyM3V7P5rMTQLP_CIs6Hx_wyfjnxE9TQKjPFHVB.N7tlQVc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ca.0Vu6sg7.........EjXkB1er4kPwN0WPw6jRsovC1vOUxpMSa9AORI3V7P5rMTQLNRv2F.VUqg4.V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44XNa.0W86sg7.........EjXkB1eZf0r4VE2pcAEEFRXKqbOEp_wbRiqNBb3V7P5rMTQLS6d9K2Pzd_7pJErSH9spC590V0DdjbggV...0Na3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.55oUXkV.........yyA.k9fRM0flV54fkLUdyeriwUOUD.nKM_ORbGAFoA2vQYDfzGTGecUiuoFFU82o_MwIcMl1C39UvuLE9rwz8unDpAvavRFBkidJvidAnSx6iYhZpc0wH9at.6_K__Zu.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.543UXkV.........yyA.k9fRM0flV54fkQy.T8wVKziEn_BQqKIiIVlcPCWxhtaKrjFJ95rzZRiqNE4pAdApUUXswjUnb5tmvFR.5RYr9G70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLK1N.54gUXkV.........yyA.k9fRM0flV54fkLTCWmZUjhhzQ8MQ3UXuSJd.FwEiiwqgxWybCf9drCLU1DLYokWptqu9hLgnsK869ldWUourBx1dp27M.3IAg.wP.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0X3.GyA1.........2vsg2.ehlR5j5.NLj0dnjbG6ixvAzaS2hEQLHQ3h2FgEhiBujxKzzvpX_GgWDWU7FsH8M9MKneo5a3iWXCfsUuNl2w98Zp67Qe16u3F8AjdJysnB3oAkKg.Ady00zSExY_ROiEMnp1jDA9rwzQr.Xt5k0XKflPRV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0WU6sg7.........EjXkB1er4kPwN0WPw5bzEqC3rjhjyOoDoxhO8gNoC1kyqsn9vbo41WhznJ_HaNCWm4WSG31HQuME_4eAuPtqEq2Z9yswjUnCYSRtV..BEx2z170...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0XO.GyA1.........2vsg2.ehlR5j5.NLj0OybufTvlx_wQqKIiuZhE25Wcq6qraMJ9_AQzahEhEALG2R66dPvavRHBcVokRJnteL1C1EvwULJbh_VWy1hzEwzdSg5hjiA9rwzQr61Qrmer7z0p9qttX6toUy4LrqbiULnt0kHzpzyySJcJQbaFvlLDcfgUrMkN2F03yWNdVV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_.qJsCFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.53VUXkV.........yyA.k9fRM0flV54fkLUdyeriwUQEsZnhPxtDb0YFoA2vQYBfeUFJ95rzYBSn4x.cRgqWCko.8k3.5Vc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0Wj6sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlztfIvImpZLp9F3E2vfjCfEOUzTxQdoI8IcImXPJGy_DXOCOk508L4m5Ft6jd3z6a8YWqabgUGxTEs3EwFQdv9uvwzQnCYO0u.C3CBIku.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_Fa.0WJ6sg7.........EjXkB1er4kPwN0WPw4bYNRd6vvQUnallI8175_XF3E2vfjCfAYc9K2Pzgj6_QyUtrFIJZxh5a6z0cJYgtRyddPt.9.ZdFkH.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wt6sg7.........EjXkB1er4kPwN0WPw6bbVDGevIgjkVZyKvui5d9F3E2vfjCfEOUA1C.7WDWU7GsqNZhF1aND1sPcMvyEd.DrE9Sthv6_bx.wDCBvLjTIZIkqvLOT2lrNTdQkq5cxf91gEr3iOSJ5V2W.fCqFV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.57s06sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlzmVpUpzOXHpI.WcPShxhOfMz98FrjSUzzZFc6oNYtCKTK_ntykM0pkROR08SEPNytuaCQ1fr3Ek7VHIUHtxkawh_Lv2sDWSiwx2SnGU57Y5t44ozQb_1zaGIiPgjhF1rUG0tMEt5dk4NK9geTV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ka.0WB6sg7.........EjXkB1er4kPwN0WPw5bXmTbq0IOUtrPm9OmKrxXF3E2vfjCfAHXdo0dyuwtrRt.9wbMvklqBAMR0F1S3GLq3V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ka.0WO6sg7.........EjXkB1er4kPwN0WPw5bXmTbq0IOUz5xx66_vyRI.lcPShxhOgK4Is6Hx_xDQA5B33VXd8ukDUEr_F5C7_xz5SVWtAc2bFN.oMYdNWc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.56wUXkV.........yyA.k9fRM0flV54fkTTT.t5fhDkzbCWX5H5FC1LVcL6rrLOLykwUKztybhBx3Rd6dy6eEZfCrpSqNVhWSRtI5x_Jva99wsLlH3kiFSYvo6qSHCK2W2mMQR6XupmNyiGq0Ati_HCcAk4zZ3g2.4IOiwd1.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.54cUXkV.........yyA.k9fRM0flV54fkPUwzNoITyoz9WmOjUGlmBH.WcQSSthOmPLbF5bvYwtI5x_Jva99LuS3mPnWk0HMafyjvBFLHiqb_.N.4krxi0c0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_sa.0W86sg7.........EjXkB1er4kPwN0WPw3b8zvSMmvQUtLPjuzgl8P8.FoCiywqgp9QbV9_vQwuIqpZJv_A9rh7dF6q_9Hr1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLR1N.553UXkV.........yyA.k9fRM0flV54fkHRbzhpUAhhz3P_uuAtDO58.FwEiiwqgiDVdJCfyHtIB5Vt2SJAeRTjrjUGltTzbODjz2CPTHvlx9bUpdTQj7xMx.77HT9oe.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Zk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.58R06sg7.........EjXkB1er4kPwN0WPw6Ea4L5hLjgEofCrpSqNgiJV7P5rMTQLTozgebRpOSPVD1fjPmswjUAG1VU7PsEobVHkOyNJQG0sHWB6POuZEHGDTYmaDcH62jCjNz2yGyDn4vuDEV6QjMPI2mTiy7klRMPVI8TuEv1OIy5zVwUKztybhDCQWsWzF2gOLiCNV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Vu6sg7.........EjXkB1er4kPwN0WPw5bzEqC3rjhbuwIeMfcjatXF3E2vfjCfBDS0V1R7VrI.V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.563UXkV.........yyA.k9fRM0flV54fkJz5qkaqYyozCv9drCLMbWAFoA2vQYDfzTTKjtzbSAgVy8Ry.ZKm8oAtW5X3Ed.lnhBklJxggNkFH3Ak2zM6P6kxYD2E074OiBkWrbvHr3og2F03sgaKFV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLPXN.53RUXkV.........yyA.k9fRM0flV54fkTSierDE4DozDZxhO4DtDn5VcL6rrLOLPhCIcAIxltliZ3qogcSJ5V.z8gXh1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_.a.0W46sg7.........EjXkB1er4kPwN0WPw4bauGvyIUhjnPmeSnK_tsNoC1kyqsnuo2GJu1ozKUbeH.MoScy.0U5n_V9.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVkB0N.4V.Q...LV72quxfmZVJLV71vrNB44bVa.0W66sg7.........EjXkB1er4kPwN0WPw5zV6XU74UvAqJbh_W513kBP5YNUQTO_Svo41WhzqMyEd0AHCS6aUg0qELI_W70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.56gUXkV.........yyA.k9fRM0flV54fkPRvtoGvjTkzzruToyowQJd.FwEiiwqgx_w3ZbkjUKkp3Rd6X1gRaQroRFX1fr8MMqfyEVIUha2lSHtQa2t1C5tnD.nKM_OR8PHTL6gkx9EvxnD7DvJGdnmGxV3.bT.Yu_c0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.58706sg7.........EjXkB1er4kPwN0WPw5bDyS3TvrgEofCrpSqNgiJV7P5rMTQLTozwcLlH3kibFY_kqX3jCfAXXhzjm2syX.2Ie9flxIbEALGITJTVWwWZDGvuGCiRv_g1lOUtw8h6gHSiCIYKXTJCvrMzntiRx_JvidAAH2cbkxzEqxnMMVP_nc.cSmWqac0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0WI6sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlUrtgyUitarFb0YFovAvQn3chTVeJhbyu9wvJjiNSmUeTeSnK_tezYxfiFeR0Q1vKZl70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.53RUXkV.........yyA.k9fRM0flV54fkQy.T8wVKzjEjtzbS2hEalYFoA2vQYEfN9TbF5bvntRyfjnxE8SRRk.VgCIl1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.57706sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlzznvTJurwvFd.FoCiywqgxdz3JYmjUGlpJFc6m3igsQ2JDo_VexmKpxezYs3rvOVwMJiLtVyIEp.JpUyUctQrY71PEC_MDv.K.yl6pqT3.rM2zJrdfZFToap0k.ZTpcxLV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44bNa.0WD6sg7.........EjXkB1er4kPwN0WPw6jRsovC1vOUtazfyn34gi8.FoCiywqgy9Xdo0dymx.lG31HNIJJth5q3yRTsa_.PpiWKcH.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFtB0N.4V.Q...LV72quxfmZVJLV71vrNB44b.a.0Wj6sg7.........EjXkB1er4kPwN0WPw6Ea4L5hLjgjvmSa45oFM4XF3E2vfjCfDYo41WhzpLgMOi8lkj0huw0uXn5dFyrDJ2Q47vB7KNUQbD7glyWMafyjf7ILl0wcQndjUvr1TZ6.COMV8Vm.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wx6sg7.........EjXkB1er4kPwN0WPw4Elhg8hczhjuYRpOTPjqx9F3E2vfjCfEOUU1xxMEbvDN8USa9AONI.G1XU37rFCrwUH1TaTAUnp3NqKFHzMOi8lrBMVWxbP_znSX91jmEkSPjR2ZAasrN6PTsb_VN.jfbgOJc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_7a.0W76sg7.........EjXkB1er4kPwN0WPw6bQehnYlIhjyOoDoxhO8gNoC1kyqsn9vMd9K2PzXjF3dLvyfHmWpFP.AnrsCk9.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ka.0Vu6sg7.........EjXkB1er4kPwN0WPw6jv6_SUNzhjysfDv64Ba8XF3E2vfjCfBDS0V2ivDMH.V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.58B06sg7.........EjXkB1er4kPwN0WPw4buUehvj6q6uMavmgvgLKXF3E2vfjCf4DVhEp6yter3nD93MlxZB9I1Asl512spX_GBagsNDOVadUVq5biUGn00mgrFj.nXYNc68a28ay7s3R78E_TycGiEeNxn_BQqKIi7jWeAmiizEq1HlyaUhIk78J5.00Au1xX.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLO1N.54cUXkV.........yyA.k9fRM0flV54fkPTA8uUN4C_zyAYmxzDRvcZ02FqvvnPnIc6HxWy_tiwfDv348csdvnmpZJr_AfcwgIFWTsYLYyOyHaZ.A_XQ7170...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aca.0WM6sg7.........EjXkB1er4kPwN0WPw4bauGvyIUhjzWTyfYmxzD8.FoCiywqgou0ojOUtiwfDv643XODX3Qc.qe933VXKWxWwoWn0vZo.BmLn0oP.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_.qJsCFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLBXN.52cUXkV.........yyA.k9fwVejr.BELVhzOwvfu6hgzsz6R4LSeEn5VcL6rrLQLcJc2.EEAPQ6P....4Y7G..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0WI6sg7.........EjXkB1er4kPwN0WPw5bDyS3TvrgblxQzbvi8hq8.FoCiywqgp9AbV9_vOziXYDpfr_6gftb9bUpdTQjcvPvo5Z.iELp.l70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.54.UXkV.........yyA.k9fRM0flV54fkTzgTKpxYyozHgrUKrOXmwH.WcQSSthORS4IcAIxGyTdYLkeSkaddnPCg8wsxl8A.k01SF_63V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFtB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0XT.GyA1.........2vsg2.ehlR5j5.NLj0ntWKWfKfvAx3mPnWB4HU5C2FgEhiBygJ95rzONE1ZS_A6qD9vwaeyr_Q5R4zai2NPTs2JoT7WijvmWU57Y5t456Dnxh94tsa7EVrlSepaMWkujymlI817BZEJlncuD2jtl4wcDiwYuoVu8sjRPQqCLwbNccMVF8X5QftiBk2.D1bXKlX.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.55VUXkV.........yyA.k9fRM0flV54fkPUwzNoITyozzruToyowQL8.FwEiiwqgtC8IcAIx_mIUHlxMzg3J0kbzUcsdfb8MMqfyEZfhlnGM.DHFKQYgFNWQGV0KMgO_6V179mLlBV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLR1N.55ZUXkV.........yyA.k9fRM0flV54fkHRbzhpUAhhzyAYmxzDRvcZ02FqvvnPnchCIcAIxGubtywdDQB5_2_DxwxG5CdLvaD81TSCvzTwYy4mq0NijRl3m4uRx0ClEAVo.Kj1c8Xc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.54.UXkV.........yyA.k9fRM0flV54fkTxnYIgoAh_z_8ezfyn3_cZ02FqvvnPnchCIcAIxGyTdYLkeSr5dcnLCR.Syxt89.k22u_oc3V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44XVa.0W76sg7.........EjXkB1esYEzo.95fFJz5Lwbq2uqUvAsDdShkO98.FoCiywqgwAc9K2Pzd_7pJErSHAcwjHa.Ut9Xzau....4XVG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0WD6sg7.........EjXkB1er4kPwN0WPw6jv6_SUNzhjwnUKrOXXyM3V7P5rMTQLM6GJu1ozGTVsVX083AeeJoYv1UDjRIH.CZcOswH.F..4YkG.."]'

// Convert JSON string to a WarpScript List
JSON->

// UNWRAP those GTS
UNWRAP

[
    SWAP // Swap is pushing the GTS into the list
    [] // Labels list to compute the equivalence class
    { 'type' 'gazole' } // filter.function parameter. To initialize a Map with one element in WarpScript: { 'key' 'value' }
    filter.bylabels // filter.function
] FILTER
```

~~~
// Wrap of the set of GTS
'["60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFsB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wm6sg7.........EjXkB1er4kPwN0WPw6bmY25_VAvnvyUtrFvItgHoC1kyqsnezoMrogUKztyEW69GuRGuZnhPxtDn32ktywfDv643dRykiQ4VFr341UDM7GuqsA4pv_gmMR6mAN7.MGt.2zGfFBu.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aca.0Wb6sg7.........EjXkB1er4kPwN0WPw3b8zvSMmvQUu_uuAtDd6dXF3E2vfjCfDYo41WhzqMyjf7ILmk8ekBeXW077emiMOi8lrBMtUPKVHr3dFurjYJRWacj9kad0k1zQa7jBV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLPXN.54VUXkV.........yyA.k9fRM0flV54fkLTQd6jtCyozzEqwnMMWuNZ02FqvvnPnIc6HxWy_tiwfDv348Zu7GiWnbhf7db9ML6q3nHEC6TIH.EvIZrVP.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Vk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.55FUXkV.........yyA.k9fRM0flV54fkTU9BBPL.jjE3F88jdRyIF_cPCWxhtbKzjD_YmhzEwyS1DLYokWp0NijRxZL39iEg6ZnFL.LdjYjtnbSnhD7CsRwSy1X.PNLBaom.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_sa.0W86sg7.........EjXkB1er4kPwN0WPw6bbVDGevIgjofCrpSqNgj3V7P5rMTQLP_CIs6Hx_ySdnPmeSm__IqZoV0DvPwo1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFsB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wp6sg7.........EjXkB1er4kPwN0WPw6bmY25_VAvAzEr_OrNNYZ_c94WxxpaKjijJa10XK.yDVpMxqLAONG.ZWx1MourwxG5C_nu18hrKlxcRna5y4TFeHdrXIUb0CWWOAjY9tShkTAfMDYm.6k4tpRu.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.56NUXkV.........yyA.k9fRM0flV54fkJz5qkaqYyozU4ntyr_DxwH.WcQSSthOoTZdJCfycxIwULJbhW0LtnmpZJr_AePsJCvoMjzv12uMQR6XuplkzcT6vih3eWsXt7r0.CBRX2u1vX2VAr8d.3YUok01.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFsB2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Vk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.563UXkV.........yyA.k9fRM0flV54fkTU9BBPL.jgE8vONGVVZIF_cPCWxhtbKzgE6_QyUtrGEWEAGPNHuhlBnXYNckEZUdTQj9nil0ORykiNxS4wbJjJFFzkY_qr0sihRl8i2rzqZoV..YJkxBV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLK1N.54cUXkV.........yyA.k9fRM0flV54fkLTCWmZUjhhz1MnS9fRYP3d.FwEiiwqgx_z9IamlY01N1DLYokWpwzT0KD8HGmgPNQxYdvbrgGMJBWR.GcHXLlc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_7a.0W96sg7.........EjXkB1er4kPwN0WPw6bQehnYlIhjwnUKrOXXyM3V7P5rMTQLP_CIs6Hx_wyfjnxE9TQKjPFHVB.N7tlQVc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ca.0Vu6sg7.........EjXkB1er4kPwN0WPw6jRsovC1vOUxpMSa9AORI3V7P5rMTQLNRv2F.VUqg4.V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44XNa.0W86sg7.........EjXkB1eZf0r4VE2pcAEEFRXKqbOEp_wbRiqNBb3V7P5rMTQLS6d9K2Pzd_7pJErSH9spC590V0DdjbggV...0Na3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.55oUXkV.........yyA.k9fRM0flV54fkLUdyeriwUOUD.nKM_ORbGAFoA2vQYDfzGTGecUiuoFFU82o_MwIcMl1C39UvuLE9rwz8unDpAvavRFBkidJvidAnSx6iYhZpc0wH9at.6_K__Zu.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.543UXkV.........yyA.k9fRM0flV54fkQy.T8wVKziEn_BQqKIiIVlcPCWxhtaKrjFJ95rzZRiqNE4pAdApUUXswjUnb5tmvFR.5RYr9G70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLK1N.54gUXkV.........yyA.k9fRM0flV54fkLTCWmZUjhhzQ8MQ3UXuSJd.FwEiiwqgxWybCf9drCLU1DLYokWptqu9hLgnsK869ldWUourBx1dp27M.3IAg.wP.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0X3.GyA1.........2vsg2.ehlR5j5.NLj0dnjbG6ixvAzaS2hEQLHQ3h2FgEhiBujxKzzvpX_GgWDWU7FsH8M9MKneo5a3iWXCfsUuNl2w98Zp67Qe16u3F8AjdJysnB3oAkKg.Ady00zSExY_ROiEMnp1jDA9rwzQr.Xt5k0XKflPRV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0WU6sg7.........EjXkB1er4kPwN0WPw5bzEqC3rjhjyOoDoxhO8gNoC1kyqsn9vbo41WhznJ_HaNCWm4WSG31HQuME_4eAuPtqEq2Z9yswjUnCYSRtV..BEx2z170...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0XO.GyA1.........2vsg2.ehlR5j5.NLj0OybufTvlx_wQqKIiuZhE25Wcq6qraMJ9_AQzahEhEALG2R66dPvavRHBcVokRJnteL1C1EvwULJbh_VWy1hzEwzdSg5hjiA9rwzQr61Qrmer7z0p9qttX6toUy4LrqbiULnt0kHzpzyySJcJQbaFvlLDcfgUrMkN2F03yWNdVV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_.qJsCFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.53VUXkV.........yyA.k9fRM0flV54fkLUdyeriwUQEsZnhPxtDb0YFoA2vQYBfeUFJ95rzYBSn4x.cRgqWCko.8k3.5Vc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0Wj6sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlztfIvImpZLp9F3E2vfjCfEOUzTxQdoI8IcImXPJGy_DXOCOk508L4m5Ft6jd3z6a8YWqabgUGxTEs3EwFQdv9uvwzQnCYO0u.C3CBIku.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kDFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_Fa.0WJ6sg7.........EjXkB1er4kPwN0WPw4bYNRd6vvQUnallI8175_XF3E2vfjCfAYc9K2Pzgj6_QyUtrFIJZxh5a6z0cJYgtRyddPt.9.ZdFkH.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wt6sg7.........EjXkB1er4kPwN0WPw6bbVDGevIgjkVZyKvui5d9F3E2vfjCfEOUA1C.7WDWU7GsqNZhF1aND1sPcMvyEd.DrE9Sthv6_bx.wDCBvLjTIZIkqvLOT2lrNTdQkq5cxf91gEr3iOSJ5V2W.fCqFV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.57s06sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlzmVpUpzOXHpI.WcPShxhOfMz98FrjSUzzZFc6oNYtCKTK_ntykM0pkROR08SEPNytuaCQ1fr3Ek7VHIUHtxkawh_Lv2sDWSiwx2SnGU57Y5t44ozQb_1zaGIiPgjhF1rUG0tMEt5dk4NK9geTV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ka.0WB6sg7.........EjXkB1er4kPwN0WPw5bXmTbq0IOUtrPm9OmKrxXF3E2vfjCfAHXdo0dyuwtrRt.9wbMvklqBAMR0F1S3GLq3V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ka.0WO6sg7.........EjXkB1er4kPwN0WPw5bXmTbq0IOUz5xx66_vyRI.lcPShxhOgK4Is6Hx_xDQA5B33VXd8ukDUEr_F5C7_xz5SVWtAc2bFN.oMYdNWc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBFGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.56wUXkV.........yyA.k9fRM0flV54fkTTT.t5fhDkzbCWX5H5FC1LVcL6rrLOLykwUKztybhBx3Rd6dy6eEZfCrpSqNVhWSRtI5x_Jva99wsLlH3kiFSYvo6qSHCK2W2mMQR6XupmNyiGq0Ati_HCcAk4zZ3g2.4IOiwd1.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.54cUXkV.........yyA.k9fRM0flV54fkPUwzNoITyoz9WmOjUGlmBH.WcQSSthOmPLbF5bvYwtI5x_Jva99LuS3mPnWk0HMafyjvBFLHiqb_.N.4krxi0c0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_sa.0W86sg7.........EjXkB1er4kPwN0WPw3b8zvSMmvQUtLPjuzgl8P8.FoCiywqgp9QbV9_vQwuIqpZJv_A9rh7dF6q_9Hr1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLR1N.553UXkV.........yyA.k9fRM0flV54fkHRbzhpUAhhz3P_uuAtDO58.FwEiiwqgiDVdJCfyHtIB5Vt2SJAeRTjrjUGltTzbODjz2CPTHvlx9bUpdTQj7xMx.77HT9oe.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tC2Zk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.58R06sg7.........EjXkB1er4kPwN0WPw6Ea4L5hLjgEofCrpSqNgiJV7P5rMTQLTozgebRpOSPVD1fjPmswjUAG1VU7PsEobVHkOyNJQG0sHWB6POuZEHGDTYmaDcH62jCjNz2yGyDn4vuDEV6QjMPI2mTiy7klRMPVI8TuEv1OIy5zVwUKztybhDCQWsWzF2gOLiCNV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Vu6sg7.........EjXkB1er4kPwN0WPw5bzEqC3rjhbuwIeMfcjatXF3E2vfjCfBDS0V1R7VrI.V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLP1N.563UXkV.........yyA.k9fRM0flV54fkJz5qkaqYyozCv9drCLMbWAFoA2vQYDfzTTKjtzbSAgVy8Ry.ZKm8oAtW5X3Ed.lnhBklJxggNkFH3Ak2zM6P6kxYD2E074OiBkWrbvHr3og2F03sgaKFV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLPXN.53RUXkV.........yyA.k9fRM0flV54fkTSierDE4DozDZxhO4DtDn5VcL6rrLOLPhCIcAIxltliZ3qogcSJ5V.z8gXh1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_.a.0W46sg7.........EjXkB1er4kPwN0WPw4bauGvyIUhjnPmeSnK_tsNoC1kyqsnuo2GJu1ozKUbeH.MoScy.0U5n_V9.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVkB0N.4V.Q...LV72quxfmZVJLV71vrNB44bVa.0W66sg7.........EjXkB1er4kPwN0WPw5zV6XU74UvAqJbh_W513kBP5YNUQTO_Svo41WhzqMyEd0AHCS6aUg0qELI_W70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.56gUXkV.........yyA.k9fRM0flV54fkPRvtoGvjTkzzruToyowQJd.FwEiiwqgx_w3ZbkjUKkp3Rd6X1gRaQroRFX1fr8MMqfyEVIUha2lSHtQa2t1C5tnD.nKM_OR8PHTL6gkx9EvxnD7DvJGdnmGxV3.bT.Yu_c0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.58706sg7.........EjXkB1er4kPwN0WPw5bDyS3TvrgEofCrpSqNgiJV7P5rMTQLTozwcLlH3kibFY_kqX3jCfAXXhzjm2syX.2Ie9flxIbEALGITJTVWwWZDGvuGCiRv_g1lOUtw8h6gHSiCIYKXTJCvrMzntiRx_JvidAAH2cbkxzEqxnMMVP_nc.cSmWqac0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0WI6sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlUrtgyUitarFb0YFovAvQn3chTVeJhbyu9wvJjiNSmUeTeSnK_tezYxfiFeR0Q1vKZl70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVkB2.kC.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.53RUXkV.........yyA.k9fRM0flV54fkQy.T8wVKzjEjtzbS2hEalYFoA2vQYEfN9TbF5bvntRyfjnxE8SRRk.VgCIl1V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCFGoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.57706sg7.........EjXkB1er4kPwN0WPw5bDqUa12qlzznvTJurwvFd.FoCiywqgxdz3JYmjUGlpJFc6m3igsQ2JDo_VexmKpxezYs3rvOVwMJiLtVyIEp.JpUyUctQrY71PEC_MDv.K.yl6pqT3.rM2zJrdfZFToap0k.ZTpcxLV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44bNa.0WD6sg7.........EjXkB1er4kPwN0WPw6jRsovC1vOUtazfyn34gi8.FoCiywqgy9Xdo0dymx.lG31HNIJJth5q3yRTsa_.PpiWKcH.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFtB0N.4V.Q...LV72quxfmZVJLV71vrNB44b.a.0Wj6sg7.........EjXkB1er4kPwN0WPw6Ea4L5hLjgjvmSa45oFM4XF3E2vfjCfDYo41WhzpLgMOi8lkj0huw0uXn5dFyrDJ2Q47vB7KNUQbD7glyWMafyjf7ILl0wcQndjUvr1TZ6.COMV8Vm.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0Wx6sg7.........EjXkB1er4kPwN0WPw4Elhg8hczhjuYRpOTPjqx9F3E2vfjCfEOUU1xxMEbvDN8USa9AONI.G1XU37rFCrwUH1TaTAUnp3NqKFHzMOi8lrBMVWxbP_znSX91jmEkSPjR2ZAasrN6PTsb_VN.jfbgOJc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lB.GoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44_7a.0W76sg7.........EjXkB1er4kPwN0WPw6bQehnYlIhjyOoDoxhO8gNoC1kyqsn9vMd9K2PzXjF3dLvyfHmWpFP.AnrsCk9.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_06CkDIV3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44_ka.0Vu6sg7.........EjXkB1er4kPwN0WPw6jv6_SUNzhjysfDv64Ba8XF3E2vfjCfBDS0V2ivDMH.V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLTXN.58B06sg7.........EjXkB1er4kPwN0WPw4buUehvj6q6uMavmgvgLKXF3E2vfjCf4DVhEp6yter3nD93MlxZB9I1Asl512spX_GBagsNDOVadUVq5biUGn00mgrFj.nXYNc68a28ay7s3R78E_TycGiEeNxn_BQqKIi7jWeAmiizEq1HlyaUhIk78J5.00Au1xX.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLO1N.54cUXkV.........yyA.k9fRM0flV54fkPTA8uUN4C_zyAYmxzDRvcZ02FqvvnPnIc6HxWy_tiwfDv348csdvnmpZJr_AfcwgIFWTsYLYyOyHaZ.A_XQ7170...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lC.GoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44aca.0WM6sg7.........EjXkB1er4kPwN0WPw4bauGvyIUhjzWTyfYmxzD8.FoCiywqgou0ojOUtiwfDv643XODX3Qc.qe933VXKWxWwoWn0vZo.BmLn0oP.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_.qJsCFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLBXN.52cUXkV.........yyA.k9fwVejr.BELVhzOwvfu6hgzsz6R4LSeEn5VcL6rrLQLcJc2.EEAPQ6P....4Y7G..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.lCkGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0WI6sg7.........EjXkB1er4kPwN0WPw5bDyS3TvrgblxQzbvi8hq8.FoCiywqgp9AbV9_vOziXYDpfr_6gftb9bUpdTQjcvPvo5Z.iELp.l70...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.54.UXkV.........yyA.k9fRM0flV54fkTzgTKpxYyozHgrUKrOXmwH.WcQSSthORS4IcAIxGyTdYLkeSkaddnPCg8wsxl8A.k01SF_63V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIFtB2.kBVGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIFtB0N.4V.Q...LV72quxfmZVJLV71vrNB44bca.0XT.GyA1.........2vsg2.ehlR5j5.NLj0ntWKWfKfvAx3mPnWB4HU5C2FgEhiBygJ95rzONE1ZS_A6qD9vwaeyr_Q5R4zai2NPTs2JoT7WijvmWU57Y5t456Dnxh94tsa7EVrlSepaMWkujymlI817BZEJlncuD2jtl4wcDiwYuoVu8sjRPQqCLwbNccMVF8X5QftiBk2.D1bXKlX.F..4YkG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kC.GoTM0_.qJlB.FiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.55VUXkV.........yyA.k9fRM0flV54fkPUwzNoITyozzruToyowQL8.FwEiiwqgtC8IcAIx_mIUHlxMzg3J0kbzUcsdfb8MMqfyEZfhlnGM.DHFKQYgFNWQGV0KMgO_6V179mLlBV3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7kB2.kD.GoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tBY.k4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLR1N.55ZUXkV.........yyA.k9fRM0flV54fkHRbzhpUAhhzyAYmxzDRvcZ02FqvvnPnchCIcAIxGubtywdDQB5_2_DxwxG5CdLvaD81TSCvzTwYy4mq0NijRl3m4uRx0ClEAVo.Kj1c8Xc0...LE03.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBVGoTM0_0aSWTaxgOFFiNM0k3M0mPMWZOMCYNM8XSM8WQbGn.aCk0I7tD2Nk4V.L.0g..0P.VEQfqj9H0GP.VAjSVkJLT1N.54.UXkV.........yyA.k9fRM0flV54fkTxnYIgoAh_z_8ezfyn3_cZ02FqvvnPnchCIcAIxGyTdYLkeSr5dcnLCR.Syxt89.k22u_oc3V3..0Nw3F.","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDI7mD2.kBFGoTM0_05SkQ5B3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDI7kB0N.4V.Q...LV72quxfmZVJLV71vrNB44XVa.0W76sg7.........EjXkB1esYEzo.95fFJz5Lwbq2uqUvAsDdShkO98.FoCiywqgwAc9K2Pzd_7pJErSHAcwjHa.Ut9Xzau....4XVG..","60VFO54oNHtaSLKgAaOmNLtYOGg4X.CkQr.0JV8dO.VmDIVqB2.kBkGoTM0_06CkDIJ3Aa4kR04kRa_sO5KnNq4mNbKmNLtoRk8YR.JmDIVqB0N.4V.Q...LV72quxfmZVJLV71vrNB44aVa.0WD6sg7.........EjXkB1er4kPwN0WPw6jv6_SUNzhjwnUKrOXXyM3V7P5rMTQLM6GJu1ozGTVsVX083AeeJoYv1UDjRIH.CZcOswH.F..4YkG.."]'

// Convert JSON string to a WarpScript List
JSON->

// UNWRAP those GTS
UNWRAP

[
  SWAP // SWAP is interverting the [ with the GTS in a elegant manner
  // Write your filter here
] FILTER