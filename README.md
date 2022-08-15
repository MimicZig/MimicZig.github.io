<html>

<head>
    <title>Vindictus Damage Calculator</title>
    <meta name="viewport" content="width=650">
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
    </style>
</head>

<body>
    <div class='container' style='width: fit-content;'>
        <hr>
        <div id='header' style='text-align: center; font-size: 30px; font-weight: bold;'>Vindictus Damage Calculator</div>
        <hr>
        <hr>
        <div id='calc' style='width: 690px; margin: 0; padding: 0;'>
            <table style='table-layout:fixed; margin: 0 auto;'>
                <col width="200px" />
                <col width="120px" />
                <tr>
                    <td nowrap>Target (Boss)</td>
                    <td>
                        <select id="boss"
                            onchange="if(this.value == 'custom') {document.querySelectorAll('.customstat').forEach(function(x){x.style.display='';});} else {document.querySelectorAll('.customstat').forEach(function(x){x.style.display='none';});}">
                            <option label="90Raids" value="lvl90raids"></option>
                            <option label="Dullahan" value="dullahan"></option>
                            <option label="Aes" value="aessidhe"></option>
                            <option label="Arcana" value="arcana"></option>
                            <option label="Rupacitus" value="rupacitus"></option>
                            <option label="Claire" value="claire"></option>
                            <option label="Elchulus" value="elchulus"></option>
                            <option label="Macha" value="macha"></option>
                            <option label="Agares" value="agares"></option>
                            <option label="Lugh" value="lugh"></option>
                            <option label="Selren" value="selren"></option>
                            <option label="Marject" value="marject"></option>
                            <option label="Aodhan" value="aodhan"></option>
                            <option label="Caesar" value="caesar"></option>
                            <option label="Nyle" value="nextboss1"></option>
                            <option label="Rag" value="nextboss2"></option>
                            <option label="Special" value="special"></option>
                            <option label="Neam" value="neamhain"></option>
                            <option label="Balor" value="balor" selected></option>
                            <option label="Brigit" value="brigit"></option>
                            <option label="Hell" value="hell"></option>
                            <option label="Custom" value="custom"></option>
                        </select>
                    </td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Boss Def</td>
                    <td><input id='bossdef' value='0'></td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Boss Crit Res</td>
                    <td><input id='bossres' value='0'></td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Boss Res(0 = CF not applied)</td>
                    <td><input id='bossdongsukres' value='0'></td>
                </tr>
                <tr class='customstat' style='display: none;'>
                    <td nowrap>Counterforce correction minimum(10 = 10 = Minimum 10% even when cf is lower)</td>
                    <td><input id='bossdongsukmindmg' value='100'></td>
                </tr>
            </table>
            <hr>
            <hr>
            <div id='calc1' style='display: inline-block; width: 340px;'>
                <div style='text-align: center;'>Character No. 1</div>
                <div id='input'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
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
                            <td nowrap>Attack Limit Removal</td>
                            <td><input id='alr' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Balance</td>
                            <td><input id='bal' value='90'></td>
                        </tr>
                        <tr>
                            <td nowrap>Crit</td>
                            <td><input id='cri' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap colspan="2" style="text-align: center;">
                                <label for='swordl1'>Sword Lann</label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="swordl1"
                                    onchange="if(this.checked)document.querySelector('#spearl1').checked = false;">
                                &nbsp;&nbsp;
                                <label for='spearl1'>Spear Lann</label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="spearl1"
                                    onchange="if(this.checked)document.querySelector('#swordl1').checked = false;">
                            </td>
                        </tr>
                        <tr>
                            <td nowrap>CF</td>
                            <td><input id='dongsuk' value='200'></td>
                        </tr>
                    </table>
                    <hr>
                    <button style='width: 324px;' onclick='exec(1);'>Character No. 1 Combat Power Calculation</button>
                </div>
                <div id='output'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Effective Combat power (without Crit)</td>
                            <td nowrap><input id='nocritdmg'><input
                                    style='width: auto; vertical-align: middle; margin-left: 7px;' type="checkbox"
                                    id="compnocrit"
                                    onchange="document.querySelector('#compcrit').checked = !(this.checked);"></td>
                        </tr>
                        <tr>
                            <td nowrap>Effective Combat Power (including Crit)</td>
                            <td nowrap><input id='critdmg'><input
                                    style='width: auto; vertical-align: middle; margin-left: 7px;' type="checkbox"
                                    id="compcrit" checked
                                    onchange="document.querySelector('#compnocrit').checked = !(this.checked);"></td>
                        </tr>
                    </table>
                </div>
            </div>
            <div id='calc2' style='display: inline-block; width: 340px;'>
                <div style='text-align: center;'>Character No. 2 </div>
                <div id='input'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
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
                            <td nowrap>Attack Limit Removal</td>
                            <td><input id='alr' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap>Balance</td>
                            <td><input id='bal' value='90'></td>
                        </tr>
                        <tr>
                            <td nowrap>Crit</td>
                            <td><input id='cri' value='0'></td>
                        </tr>
                        <tr>
                            <td nowrap colspan="2" style="text-align: center;">
                                <label for='swordl2'>Sword Lann</label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="swordl2"
                                    onchange="if(this.checked)document.querySelector('#spearl2').checked = false;">
                                &nbsp;&nbsp;
                                <label for='spearl2'>Spear Lann</label><input
                                    style='width: auto; vertical-align: middle; margin-left: 3px;' type="checkbox"
                                    id="spearl2"
                                    onchange="if(this.checked)document.querySelector('#swordl2').checked = false;">
                            </td>
                        </tr>
                        <tr>
                            <td nowrap>CF</td>
                            <td><input id='dongsuk' value='200'></td>
                        </tr>
                    </table>
                    <hr>
                    <button style='width: 324px;' onclick='exec(2);'>Character No. 2 Combat Power Calculation</button>
                </div>
                <div id='output'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>Effective Combat power (without Crit)</td>
                            <td><input id='nocritdmg'></td>
                        </tr>
                        <tr>
                            <td nowrap>Effective Combat Power (including Crit)</td>
                            <td><input id='critdmg'></td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <hr>
        <div id='footer'
            style='width: fit-content; margin: 0 auto; text-size-adjust:none; font-weight: bold; text-align: center;'>
            ↑&nbsp;&nbsp;&nbsp;&nbsp;<br />
            To use the following calculator, select the counterforce that you want to use as a priority.
        </div>
        <hr>
        <hr>
        <div id='appendix' style='text-align: center; font-size: 22px; font-weight: bold;'>Vindictus Damage Corrector <span
                style="color:red">(only for reference)</span></div>
        <hr>
        <hr>
        <div id='footer'
            style='width: fit-content; margin: 0 auto; text-size-adjust:none; font-weight: bold; font-size: 14px; '>
            <span style="color:red">T</span>he result value of the calculator may always be different from the actual value, please use it for reference only.<br />
            <span style="color:red">M</span>ost case party and solo dps is different so please look at solo clear time for fun.<br />
            <span style="color:red">A</span>lso, Lann and cestus has different damage calculation with critical rate<br />
            Than other characters so same stat comparison can be meaningless.<br />
        </div>
        <hr>
        <hr>
        <div id='compare' style='width: 690px; margin: 0; padding: 0;'>
            <div id='input'>
                <div id='comp1' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter before adjusting</td>
                            <td nowrap><input id='deal1' value='50'>%</td>
                        </tr>
                    </table>
                </div>
                <div id='comp2' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>DMG meter before adjusting</td>
                            <td nowrap><input id='deal2' value='50'>%</td>
                        </tr>
                    </table>
                </div>
                <button style='display: block; width: 100%;' onclick='compare();'>선택한 유효전투력 기준으로 동스펙 2인 플레이시 딜량
                    보정해보기</button>
            </div>
            <div id='output'>
                <div id='comp1' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>보정 후 딜량</td>
                            <td nowrap><input id='deal1'>%</td>
                        </tr>
                    </table>
                </div>
                <div id='comp2' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="200px" />
                        <col width="120px" />
                        <tr>
                            <td nowrap>보정 후 딜량</td>
                            <td nowrap><input id='deal2'>%</td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <hr>
        <div id='timecalc' style='width: 690px; margin: 0; padding: 0;'>
            <div id='input'>
                <div id='time1' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="150px" />
                        <col width="170px" />
                        <tr>
                            <td nowrap>보정 전 클탐</td>
                            <td nowrap><input id='min1' value='30'>분 <input id='sec1' value='00'>초</td>
                        </tr>
                        <tr>
                            <td nowrap>본인 딜량</td>
                            <td nowrap><input id='timedeal1' value='100'>%</td>
                        </tr>
                    </table>
                    <button style='display: block; width: 100%;' onclick='timecalc(1);'>풀스펙(6400/3550) 기준 분당딜, 솔플 클탐
                        계산하기</button>
                </div>
                <div id='time2' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="150px" />
                        <col width="170px" />
                        <tr>
                            <td nowrap>보정 전 클탐</td>
                            <td nowrap><input id='min2' value='30'>분 <input id='sec2' value='00'>초</td>
                        </tr>
                        <tr>
                            <td nowrap>본인 딜량</td>
                            <td nowrap><input id='timedeal2' value='100'>%</td>
                        </tr>
                    </table>
                    <button style='display: block; width: 100%;' onclick='timecalc(2);'>풀스펙(6400/3550) 기준 분당딜, 솔플 클탐
                        계산하기</button>
                </div>
            </div>
            <div id='output'>
                <div id='time1' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="150px" />
                        <col width="170px" />
                        <tr>
                            <td nowrap>보정 후 분당딜</td>
                            <td nowrap><input id='dpm1' value=''>%</td>
                        </tr>
                        <tr>
                            <td nowrap>└▶ 솔플 클탐</td>
                            <td nowrap><input id='min1' value=''>분 <input id='sec1' value=''>초</td>
                        </tr>
                    </table>
                </div>
                <div id='time2' style='display: inline-block; width: 340px;'>
                    <table style='table-layout:fixed;'>
                        <col width="150px" />
                        <col width="170px" />
                        <tr>
                            <td nowrap>보정 후 분당딜</td>
                            <td nowrap><input id='dpm2' value=''>%</td>
                        </tr>
                        <tr>
                            <td nowrap>└▶ 솔플 클탐</td>
                            <td nowrap><input id='min2' value=''>분 <input id='sec2' value=''>초</td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <hr>
        <hr>
        <div id='footer' style='width: fit-content; margin: 0 auto; text-size-adjust:none; font-weight: bold;'>
            본 계산기의 데미지 계산식은 <a style="color: black;" href='http://www.inven.co.kr/board/heroes/2028/38144'
                target='blank'>http://www.inven.co.kr/boa...</a> 글을 참고했습니다.
        </div>
    </div>
</body>

</html>
