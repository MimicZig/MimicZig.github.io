<!DOCTYPE html>
<html>
<head>
    <title>Vindictus Damage Calculator</title>
    <meta name="viewport" content="width=1000">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <link rel="icon" href="favicon.ico" type="image/x-icon">
    <script src="calc.js"></script>
    <style>
        select {
            width: 100%;
            margin: 0;
            padding: 0;
}

input {
            width: calc(100% - 4px);
            margin: 0;
            padding: 0;
        }

        #timecalc input {
            width: calc(50% - 20px);
            margin: 0;
            padding: 0;
        }

        input#timedeal1,
        input#timedeal2,
        input#dpm1,
        input#dpm2 {
            width: calc(100% - 4px);
            margin: 0;
            padding: 0;
        }

        tr td:first-child {
            padding-left: 10px;
        }

.content {
  max-width: 800px;
  margin: auto;
  background: white;
  padding: 10px;
}
</style>

<body>

<div class="content">

</head>

<body>
    <div class='container' style='width: fit-content;'>
        <hr>
        <div id='header' style='text-align: center; font-size: 30px; font-weight: bold;'>Vindictus Damage Calcuator</div>
        <hr>
        <hr>
        <div id='calc' style='width: 800px; margin: 0; padding: 0;'>
            <table style='table-layout:fixed; margin: 0 auto;'>
                <col width="200px" />
                <col width="120px" />
                <tr>
                    <td nowrap>Select Boss</td>
                    <td>
                        <select id="boss"
                            onchange="if(this.value == 'custom') {document.querySelectorAll('.customstat').forEach(function(x){x.style.display='';});} else {document.querySelectorAll('.customstat').forEach(function(x){x.style.display='none';});}">
                            <option label="Level 90 Raids" value="lvl90raids"></option>
                            <option label="Dullahan" value="dullahan"></option>
                            <option label="Aes Sidhe" value="aessidhe"></option>
                            <option label="Arcana" value="arcana"></option>
                            <option label="Rupacitus" value="rupacitus"></option>
                            <option label="Claire" value="claire"></option>
                            <option label="Outraged Elchulus" value="elchulus"></option>
                            <option label="Macha" value="macha"></option>
                            <option label="Agares" value="agares"></option>
                            <option label="Brilliant Lugh" value="lugh"></option>
                            <option label="Selren" value="selren"></option>
                            <option label="Marject" value="marject"></option>
                            <option label="Aodhan" value="aodhan"></option>
                            <option label="Cesar" value="caesar"></option>
                            <option label="Specials" value="special"></option>
                            <option label="Neamhain" value="neamhain"></option>
                            <option label="Balor" value="balor" selected></option>
                            <option label="Brigid" value="brigit"></option>
                            <option label="[Hell] Redeemer" value="hell"></option>
                            <option label="Nyle" value="nyle"></option>
                            <option label="Rag" value="siethe"></option>
                            <option label="Custom" value="custom"></option>
                        </select>
                    </td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Boss Defense</td>
                    <td><input id='bossdef' value='0'></td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Boss Critical Resistance</td>
                    <td><input id='bossres' value='0'></td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Boss Counterforce Resistance</td>
                    <td><input id='bossdongsukres' value='0'></td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>10 = minimum 10% even when cf is lower</td>
                    <td><input id='bossdongsukmindmg' value='30'></td>
                </tr>
            </table>
            <hr>
            <hr>
            <div id='calc1' style='display: inline-block; width: 398px;'>
                <div style='text-align: center;'>Player 1</div>
                <div id='input'>
                    <table style='table-layout:fixed;'>
                        <col width="275px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Attack</td>
                            <td><input id='atk' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Additional Damage</td>
                            <td><input id='add' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>ATT Limit</td>
                            <td><input id='alr' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Balance</td>
                            <td><input id='bal' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Critical</td>
                            <td><input id='cri' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap colspan="2" style="text-align: center;">
                                <label for='swordl1'>Sword Lann </label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="swordl1"
                                    onchange="if(this.checked)document.querySelector('#spearl1').checked = false;">
                                &nbsp;&nbsp;
                                <label for='spearl1'>Spear Lann </label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="spearl1"
                                    onchange="if(this.checked)document.querySelector('#swordl1').checked = false;">
                            </td>
                        </tr>
                        <tr>
                            <td nowrap>Counterforce</td>
                            <td><input id='dongsuk' value='0'></td>
                        </tr>
                    </table>
                    <hr>
                    <button style='width: 398px;' onclick='exec(1);'>Calculate Effective Combat Power</button>
                </div>
                <div id='output'>
                    <table style='table-layout:fixed;'>
                        <col width="250px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Effective Damage (No Crit)</td>
                            <td nowrap><input id='nocritdmg'disabled>
                            <input
                                    style='width: auto; vertical-align: middle; margin-left: 7px;' type="checkbox"
                                    id="compnocrit"
                                    onchange="document.querySelector('#compcrit').checked = !(this.checked);"></td>
                        </tr>
                            </td>
                        </tr>
                        <tr>
                            <td nowrap>Effective Damage (Crit)</td>
                            <td nowrap><input id='critdmg'disabled>
                            <input
                                    style='width: auto; vertical-align: middle; margin-left: 7px;' type="checkbox"
                                    id="compcrit" checked
                                    onchange="document.querySelector('#compnocrit').checked = !(this.checked);"></td>
                        </tr>
                            </td>
                        </tr>
                    </table>
                </div>
            </div>
            <div id='calc2' style='display: inline-block; width: 398px;'>
                <div style='text-align: center;'>Player 2</div>
                <div id='input'>
                    <table style='table-layout:fixed;'>
                        <col width="275px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Attack</td>
                            <td><input id='atk' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Additional DMG</td>
                            <td><input id='add' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>ATT Limit</td>
                            <td><input id='alr' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Balance</td>
                            <td><input id='bal' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Critical</td>
                            <td><input id='cri' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap colspan="2" style="text-align: center;">
                                <label for='swordl2'>Sword Lann </label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="swordl2"
                                    onchange="if(this.checked)document.querySelector('#spearl2').checked = false;">
                                &nbsp;&nbsp;
                                <label for='spearl2'>Spear Lann </label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="spearl2"
                                    onchange="if(this.checked)document.querySelector('#swordl2').checked = false;">
                            </td>
                        </tr>
                        <tr>
                            <td nowrap>Counterforce</td>
                            <td><input id='dongsuk' value='0'></td>
                        </tr>
                    </table>
                    <hr>
                    <button style='width: 398px;' onclick='exec(2);'>Calculate Effective Combat Power</button>
                </div>
                <div id='output'>
                    <table style='table-layout:fixed;'>
                        <col width="300px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Effective Damage (No Crit)</td>
                            <td><input id='nocritdmg'disabled></td>
                        </tr>
                        <tr>
                            <td nowrap>Effective Damage (Crit)</td>
                            <td><input id='critdmg'disabled></td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <hr>
        <div id='footer'
            style='width: fit-content; margin: 0 auto; text-size-adjust:none; font-weight: bold; text-align: center;'>
            ???&nbsp;&nbsp;&nbsp;&nbsp;<br />
            To use the following calculator, select the counterforce that you want to use as a priority.
        </div>
        <hr>
        <hr>
        <div id='appendix' style='text-align: center; font-size: 35px; font-weight: bold;'>Vindictus Damage Calculator <span
                style="color:red">(Damage is an estimate)</span></div>
        <hr>
        <hr>
        <div id='footer'
            style='width: fit-content; margin: 0 auto; text-size-adjust:none; font-weight: bold; text-align: center; font-size: 16px;  '>
            The result value of the calibrator may always be different from the actual value, please use it for reference only.<br />
            Most case party and solo dps is different so please look at solo clear time for fun
            <br />
           laan and cestus has differnt damage calculation with critical rate than other characters so same stat comparison can be meaningless
            <br />
  
        </div>
        <hr>
        <hr>
        <div id='compare' style='width: 800px; margin: 0; padding: 0;'>
            <div id='input'>
                <div id='comp1' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter before adjustment</td>
                            <td nowrap><input id='deal1' value='0'> %</td>
                        </tr>
                    </table>
                </div>
                <div id='comp2' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter before adjustment</td>
                            <td nowrap><input id='deal2' value='0'> %</td>
                        </tr>
                    </table>
                </div>
                <button style='display: block; width: 100%;' onclick='compare();'>Calculate Scaled Damage Difference.</button>
            </div>
            <div id='output'>
                <div id='comp1' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter after adjustment</td>
                            <td nowrap><input id='deal1'disabled> %</td>
                        </tr>
                    </table>
                </div>
                <div id='comp2' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter after adjustment</td>
                            <td nowrap><input id='deal2'disabled> %</td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <hr>
        <div id='timecalc' style='width: 800px; margin: 0; padding: 0;'>
            <div id='input'>
                <div id='time1' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Time</td>
                            <td nowrap><input id='min1' value='0'>Minutes <input id='sec1' value='0'>Seconds</td>
                        </tr>
                        <tr>
                            <td nowrap>DMG meter before adjustment</td>
                            <td nowrap><input id='timedeal1' value='0'>%</td>
                        </tr>
                    </table>
                    <button style='display: block; width: 100%;' onclick='timecalc(1);'>Calculate Damage With (6000 AD, 3550 ALR)</button>
                </div>
                <div id='time2' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Time</td>
                            <td nowrap><input id='min2' value='0'>Minutes <input id='sec2' value='0'>Seconds</td>
                        </tr>
                        <tr>
                            <td nowrap>DMG meter before adjustment</td>
                            <td nowrap><input id='timedeal2' value='0'>%</td>
                        </tr>
                    </table>
                    <button style='display: block; width: 100%;' onclick='timecalc(2);'>Calcuate Damage with (6000 AD, 3550 ALR)</button>
                </div>
            </div>
            <div id='output'>
                <div id='time1' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter after adjustment</td>
                            <td nowrap><input id='dpm1' value='' disabled >%</td>
                        </tr>
                        <tr>
                            <td nowrap>?????? Time</td>
                            <td nowrap><input id='min1' value='' disabled >Minutes <input id='sec1' value='' disabled >Seconds</td>
                        </tr>
                    </table>
                </div>
                <div id='time2' style='display: inline-block; width: 398px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter after adjustment</td>
                            <td nowrap><input id='dpm2' value='' disabled >%</td>
                        </tr>
                        <tr>
                            <td nowrap>?????? Time</td>
                            <td nowrap><input id='min2' value='' disabled>Minutes <input id='sec2' value=''disabled >Seconds</td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <hr>
        <hr>
        <div id='footer' style='width: fit-content; margin: 0 auto; text-size-adjust:none; font-weight: bold;'>
            The damage calculation of this calculator is based on this <a style="color: black;" href='http://www.inven.co.kr/board/heroes/2028/38144'
                target='blank'>http://www.inven.co.kr/board/heroes/2028/38144</a> 
        </div>
</div>

</body>
</html>
