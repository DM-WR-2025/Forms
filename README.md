<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DM Wheelchair Registration Form</title>
    <style>
        /* Same styling as before */

        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f7fa;
            margin: 0;
            padding: 0;
        }

        .container {
            width: 60%;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin-top: 50px;
        }

        h2 {
            text-align: center;
            color: red;
            font-size: 24px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        }

        label {
            font-size: 16px;
            margin: 10px 0;
            color: #555;
            display: block;
        }

        input, select, button {
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: 16px;
        }

        .medium-input {
            width: 50%;
            display: inline-block;
        }

        input[type="radio"] {
            width: auto;
            margin-right: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .radio-group {
            display: flex;
            align-items: center;
        }

        .radio-group label {
            margin-right: 20px;
        }

        button {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 18px;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #0056b3;
        }

        .form-group select {
            width: auto;
            display: inline-block;
            width: 50%;
        }

        .form-group input[type="file"] {
            padding: 5px;
        }

        .hidden {
            display: none;
        }

        .form-section {
            margin-bottom: 20px;
        }

        .form-section label {
            font-weight: bold;
        }

        .wheelchair-select {
            display: inline-block;
            width: 100%;
            padding: 10px;
        }

        .wheelchair-select select {
            width: 50%;
        }

        .footer {
            text-align: center;
            font-size: 14px;
            color: #777;
            margin-top: 40px;
        }

        /* Media Queries for Responsiveness */
        @media (max-width: 768px) {
            .container {
                width: 90%;
            }

            h2 {
                font-size: 20px;
            }

            .medium-input {
                width: 100%;
                display: block;
            }

            .form-group select, .form-group input {
                width: 100%;
            }

            button {
                width: 100%;
            }

            .form-group input[type="file"] {
                width: 100%;
            }

            .wheelchair-select select {
                width: 100%;
            }
        }

        @media (max-width: 480px) {
            h2 {
                font-size: 18px;
            }

            label {
                font-size: 14px;
            }

            input, select, button {
                font-size: 14px;
            }

            .medium-input {
                width: 100%;
            }

            .form-group select, .form-group input {
                font-size: 14px;
            }

            .radio-group label {
                font-size: 14px;
            }

            button {
                font-size: 16px;
            }
        }
    </style>
    <script>
        function showWheelchairOptions() {
            var desk = document.getElementById("desk").value;
            var wheelchairSelect = document.getElementById("wheelchair-options");
            wheelchairSelect.innerHTML = ""; // Clear current options

            var wheelchairOptions = {
                "BA": ["1", "2", "3"],
                "F": ["4", "5", "6"],
                "H": ["7", "8", "9"],
                "GA": ["10", "11"],
                "GD": ["12", "13"]
            };

            if (wheelchairOptions[desk]) {
                wheelchairOptions[desk].forEach(function(option) {
                    var optionElement = document.createElement("option");
                    optionElement.value = option;
                    optionElement.textContent = "Wheelchair " + option;
                    wheelchairSelect.appendChild(optionElement);
                });
            }
        }

        function toggleSecurityDepositOptions() {
            var selectedDeposit = document.querySelector('input[name="deposit-type"]:checked').value;
            document.getElementById("id-fields").style.display = "none";
            document.getElementById("cash-fields").style.display = "none";
            document.getElementById("handed-over-fields").style.display = "none";

            if (selectedDeposit === "id-license") {
                document.getElementById("id-fields").style.display = "block";
            } else if (selectedDeposit === "cash") {
                document.getElementById("cash-fields").style.display = "block";
            } else if (selectedDeposit === "security") {
                document.getElementById("handed-over-fields").style.display = "block";
            }
        }

        // Call the functions when the page is loaded to ensure that hidden fields are correctly initialized
        window.onload = function() {
            toggleSecurityDepositOptions();
        };
    </script>
</head>
<body>
    <div class="container">
        <h2>DM Wheelchair Registration Form</h2>
        <form action="https://script.google.com/macros/s/AKfycbzd_f31UDPo3AmaSlIT1QN0Tb9FwFNBaIPhsWY3BuMIBhV5oe5JR0PL_gPAhDVFuWXTsQ/exec" method="POST" enctype="multipart/form-data" onsubmit="return confirmSubmission()">
           
            <!-- Customer Name First -->
            <div class="form-group">
                <label for="customer-name">Customer Name:</label>
                <input type="text" id="customer-name" name="customer-name" required class="medium-input">
            </div>

            <!-- Nationality Dropdown Next with Full Country Names -->
           <div class="form-group">
    <label for="nationality">Nationality:</label>
    <select id="nationality" name="nationality" required>
        <option value="" disabled selected>Select Nationality</option>

        <!-- GCC Countries -->
        <option value="Bahrain (+973)">Bahrain (+973)</option>
        <option value="Kuwait (+965)">Kuwait (+965)</option>
        <option value="Oman (+968)">Oman (+968)</option>
        <option value="Qatar (+974)">Qatar (+974)</option>
        <option value="Saudi Arabia (+966)">Saudi Arabia (+966)</option>
        <option value="United Arab Emirates (+971)">United Arab Emirates (+971)</option>

        <!-- Other Countries (A to Z) -->
        <option value="Afghanistan (+93)">Afghanistan (+93)</option>
        <option value="Albania (+355)">Albania (+355)</option>
        <option value="Algeria (+213)">Algeria (+213)</option>
        <option value="Andorra (+376)">Andorra (+376)</option>
        <option value="Angola (+244)">Angola (+244)</option>
        <option value="Antigua and Barbuda (+1-268)">Antigua and Barbuda (+1-268)</option>
        <option value="Argentina (+54)">Argentina (+54)</option>
        <option value="Armenia (+374)">Armenia (+374)</option>
        <option value="Australia (+61)">Australia (+61)</option>
        <option value="Austria (+43)">Austria (+43)</option>
        <option value="Azerbaijan (+994)">Azerbaijan (+994)</option>
        <option value="Bahamas (+1-242)">Bahamas (+1-242)</option>
        <option value="Bangladesh (+880)">Bangladesh (+880)</option>
        <option value="Barbados (+1-246)">Barbados (+1-246)</option>
        <option value="Belarus (+375)">Belarus (+375)</option>
        <option value="Belgium (+32)">Belgium (+32)</option>
        <option value="Belize (+501)">Belize (+501)</option>
        <option value="Benin (+229)">Benin (+229)</option>
        <option value="Bhutan (+975)">Bhutan (+975)</option>
        <option value="Bolivia (+591)">Bolivia (+591)</option>
        <option value="Bosnia and Herzegovina (+387)">Bosnia and Herzegovina (+387)</option>
        <option value="Botswana (+267)">Botswana (+267)</option>
        <option value="Brazil (+55)">Brazil (+55)</option>
        <option value="Brunei (+673)">Brunei (+673)</option>
        <option value="Bulgaria (+359)">Bulgaria (+359)</option>
        <option value="Burkina Faso (+226)">Burkina Faso (+226)</option>
        <option value="Burundi (+257)">Burundi (+257)</option>
        <option value="Cabo Verde (+238)">Cabo Verde (+238)</option>
        <option value="Cambodia (+855)">Cambodia (+855)</option>
        <option value="Cameroon (+237)">Cameroon (+237)</option>
        <option value="Canada (+1)">Canada (+1)</option>
        <option value="Central African Republic (+236)">Central African Republic (+236)</option>
        <option value="Chad (+235)">Chad (+235)</option>
        <option value="Chile (+56)">Chile (+56)</option>
        <option value="China (+86)">China (+86)</option>
        <option value="Colombia (+57)">Colombia (+57)</option>
        <option value="Comoros (+269)">Comoros (+269)</option>
        <option value="Congo (+242)">Congo (+242)</option>
        <option value="Congo, Democratic Republic of the (+243)">Congo, Democratic Republic of the (+243)</option>
        <option value="Costa Rica (+506)">Costa Rica (+506)</option>
        <option value="Croatia (+385)">Croatia (+385)</option>
        <option value="Cuba (+53)">Cuba (+53)</option>
        <option value="Cyprus (+357)">Cyprus (+357)</option>
        <option value="Czech Republic (+420)">Czech Republic (+420)</option>
        <option value="Denmark (+45)">Denmark (+45)</option>
        <option value="Djibouti (+253)">Djibouti (+253)</option>
        <option value="Dominica (+1-767)">Dominica (+1-767)</option>
        <option value="Dominican Republic (+1-809)">Dominican Republic (+1-809)</option>
        <option value="Ecuador (+593)">Ecuador (+593)</option>
        <option value="Egypt (+20)">Egypt (+20)</option>
        <option value="El Salvador (+503)">El Salvador (+503)</option>
        <option value="Equatorial Guinea (+240)">Equatorial Guinea (+240)</option>
        <option value="Eritrea (+291)">Eritrea (+291)</option>
        <option value="Estonia (+372)">Estonia (+372)</option>
        <option value="Eswatini (+268)">Eswatini (+268)</option>
        <option value="Ethiopia (+251)">Ethiopia (+251)</option>
        <option value="Fiji (+679)">Fiji (+679)</option>
        <option value="Finland (+358)">Finland (+358)</option>
        <option value="France (+33)">France (+33)</option>
        <option value="Gabon (+241)">Gabon (+241)</option>
        <option value="Gambia (+220)">Gambia (+220)</option>
        <option value="Georgia (+995)">Georgia (+995)</option>
        <option value="Germany (+49)">Germany (+49)</option>
        <option value="Ghana (+233)">Ghana (+233)</option>
        <option value="Greece (+30)">Greece (+30)</option>
        <option value="Grenada (+1-473)">Grenada (+1-473)</option>
        <option value="Guatemala (+502)">Guatemala (+502)</option>
        <option value="Guinea (+224)">Guinea (+224)</option>
        <option value="Guinea-Bissau (+245)">Guinea-Bissau (+245)</option>
        <option value="Guyana (+592)">Guyana (+592)</option>
        <option value="Haiti (+509)">Haiti (+509)</option>
        <option value="Honduras (+504)">Honduras (+504)</option>
        <option value="Hungary (+36)">Hungary (+36)</option>
        <option value="Iceland (+354)">Iceland (+354)</option>
        <option value="India (+91)">India (+91)</option>
        <option value="Indonesia (+62)">Indonesia (+62)</option>
        <option value="Iran (+98)">Iran (+98)</option>
        <option value="Iraq (+964)">Iraq (+964)</option>
        <option value="Ireland (+353)">Ireland (+353)</option>
        <option value="Israel (+972)">Israel (+972)</option>
        <option value="Italy (+39)">Italy (+39)</option>
        <option value="Jamaica (+1-876)">Jamaica (+1-876)</option>
        <option value="Japan (+81)">Japan (+81)</option>
        <option value="Jordan (+962)">Jordan (+962)</option>
        <option value="Kazakhstan (+7)">Kazakhstan (+7)</option>
        <option value="Kenya (+254)">Kenya (+254)</option>
        <option value="Kiribati (+686)">Kiribati (+686)</option>
        <option value="Korea, North (+850)">Korea, North (+850)</option>
        <option value="Korea, South (+82)">Korea, South (+82)</option>
        <option value="Kuwait (+965)">Kuwait (+965)</option>
        <option value="Kyrgyzstan (+996)">Kyrgyzstan (+996)</option>
        <option value="Laos (+856)">Laos (+856)</option>
        <option value="Latvia (+371)">Latvia (+371)</option>
        <option value="Lebanon (+961)">Lebanon (+961)</option>
        <option value="Lesotho (+266)">Lesotho (+266)</option>
        <option value="Liberia (+231)">Liberia (+231)</option>
        <option value="Libya (+218)">Libya (+218)</option>
        <option value="Liechtenstein (+423)">Liechtenstein (+423)</option>
        <option value="Lithuania (+370)">Lithuania (+370)</option>
        <option value="Luxembourg (+352)">Luxembourg (+352)</option>
        <option value="Madagascar (+261)">Madagascar (+261)</option>
        <option value="Malawi (+265)">Malawi (+265)</option>
        <option value="Malaysia (+60)">Malaysia (+60)</option>
        <option value="Maldives (+960)">Maldives (+960)</option>
        <option value="Mali (+223)">Mali (+223)</option>
        <option value="Malta (+356)">Malta (+356)</option>
        <option value="Marshall Islands (+692)">Marshall Islands (+692)</option>
        <option value="Mauritania (+222)">Mauritania (+222)</option>
        <option value="Mauritius (+230)">Mauritius (+230)</option>
        <option value="Mexico (+52)">Mexico (+52)</option>
        <option value="Micronesia (+691)">Micronesia (+691)</option>
        <option value="Moldova (+373)">Moldova (+373)</option>
        <option value="Monaco (+377)">Monaco (+377)</option>
        <option value="Mongolia (+976)">Mongolia (+976)</option>
        <option value="Montenegro (+382)">Montenegro (+382)</option>
        <option value="Morocco (+212)">Morocco (+212)</option>
        <option value="Mozambique (+258)">Mozambique (+258)</option>
        <option value="Myanmar (+95)">Myanmar (+95)</option>
        <option value="Namibia (+264)">Namibia (+264)</option>
        <option value="Nauru (+674)">Nauru (+674)</option>
        <option value="Nepal (+977)">Nepal (+977)</option>
        <option value="Netherlands (+31)">Netherlands (+31)</option>
        <option value="New Zealand (+64)">New Zealand (+64)</option>
        <option value="Nicaragua (+505)">Nicaragua (+505)</option>
        <option value="Niger (+227)">Niger (+227)</option>
        <option value="Nigeria (+234)">Nigeria (+234)</option>
        <option value="North Macedonia (+389)">North Macedonia (+389)</option>
        <option value="Norway (+47)">Norway (+47)</option>
        <option value="Oman (+968)">Oman (+968)</option>
        <option value="Pakistan (+92)">Pakistan (+92)</option>
        <option value="Palau (+680)">Palau (+680)</option>
        <option value="Panama (+507)">Panama (+507)</option>
        <option value="Papua New Guinea (+675)">Papua New Guinea (+675)</option>
        <option value="Paraguay (+595)">Paraguay (+595)</option>
        <option value="Peru (+51)">Peru (+51)</option>
        <option value="Philippines (+63)">Philippines (+63)</option>
        <option value="Poland (+48)">Poland (+48)</option>
        <option value="Portugal (+351)">Portugal (+351)</option>
        <option value="Qatar (+974)">Qatar (+974)</option>
        <option value="Romania (+40)">Romania (+40)</option>
        <option value="Russia (+7)">Russia (+7)</option>
        <option value="Rwanda (+250)">Rwanda (+250)</option>
        <option value="Saint Kitts and Nevis (+1-869)">Saint Kitts and Nevis (+1-869)</option>
        <option value="Saint Lucia (+1-758)">Saint Lucia (+1-758)</option>
        <option value="Saint Vincent and the Grenadines (+1-784)">Saint Vincent and the Grenadines (+1-784)</option>
        <option value="Samoa (+685)">Samoa (+685)</option>
        <option value="San Marino (+378)">San Marino (+378)</option>
        <option value="Sao Tome and Principe (+239)">Sao Tome and Principe (+239)</option>
        <option value="Saudi Arabia (+966)">Saudi Arabia (+966)</option>
        <option value="Senegal (+221)">Senegal (+221)</option>
        <option value="Serbia (+381)">Serbia (+381)</option>
        <option value="Seychelles (+248)">Seychelles (+248)</option>
        <option value="Sierra Leone (+232)">Sierra Leone (+232)</option>
        <option value="Singapore (+65)">Singapore (+65)</option>
        <option value="Slovakia (+421)">Slovakia (+421)</option>
        <option value="Slovenia (+386)">Slovenia (+386)</option>
        <option value="Solomon Islands (+677)">Solomon Islands (+677)</option>
        <option value="Somalia (+252)">Somalia (+252)</option>
        <option value="South Africa (+27)">South Africa (+27)</option>
        <option value="South Korea (+82)">South Korea (+82)</option>
        <option value="South Sudan (+211)">South Sudan (+211)</option>
        <option value="Spain (+34)">Spain (+34)</option>
        <option value="Sri Lanka (+94)">Sri Lanka (+94)</option>
        <option value="Sudan (+249)">Sudan (+249)</option>
        <option value="Suriname (+597)">Suriname (+597)</option>
        <option value="Sweden (+46)">Sweden (+46)</option>
        <option value="Switzerland (+41)">Switzerland (+41)</option>
        <option value="Syria (+963)">Syria (+963)</option>
        <option value="Taiwan (+886)">Taiwan (+886)</option>
        <option value="Tajikistan (+992)">Tajikistan (+992)</option>
        <option value="Tanzania (+255)">Tanzania (+255)</option>
        <option value="Thailand (+66)">Thailand (+66)</option>
        <option value="Togo (+228)">Togo (+228)</option>
        <option value="Tonga (+676)">Tonga (+676)</option>
        <option value="Trinidad and Tobago (+1-868)">Trinidad and Tobago (+1-868)</option>
        <option value="Tunisia (+216)">Tunisia (+216)</option>
        <option value="Turkey (+90)">Turkey (+90)</option>
        <option value="Turkmenistan (+993)">Turkmenistan (+993)</option>
        <option value="Tuvalu (+688)">Tuvalu (+688)</option>
        <option value="Uganda (+256)">Uganda (+256)</option>
        <option value="Ukraine (+380)">Ukraine (+380)</option>
        <option value="United Kingdom (+44)">United Kingdom (+44)</option>
        <option value="United States (+1)">United States (+1)</option>
        <option value="Uruguay (+598)">Uruguay (+598)</option>
        <option value="Uzbekistan (+998)">Uzbekistan (+998)</option>
        <option value="Vanuatu (+678)">Vanuatu (+678)</option>
        <option value="Vatican City (+379)">Vatican City (+379)</option>
        <option value="Venezuela (+58)">Venezuela (+58)</option>
        <option value="Vietnam (+84)">Vietnam (+84)</option>
        <option value="Yemen (+967)">Yemen (+967)</option>
        <option value="Zambia (+260)">Zambia (+260)</option>
        <option value="Zimbabwe (+263)">Zimbabwe (+263)</option>
    </select>
</div>


            <!-- Phone Number Next -->
            <div class="form-group">
                <label for="phone">Phone Number:</label>
                <input type="tel" id="phone" name="phone" required class="medium-input">
            </div>
            <div class="form-group">
                 <label for="email">Customer Email:</label>
                 <input type="email" id="email" name="email" required class="medium-input">
            </div>

            <!-- Desk Selection -->
            <div class="form-group">
                <label for="desk">Select Desk:</label>
                <select id="desk" name="desk" onchange="showWheelchairOptions()" required>
                    <option value="" disabled selected>Select a desk</option>
                    <option value="BA">BA Desk</option>
                    <option value="F">F Desk</option>
                    <option value="H">H Desk</option>
                    <option value="GA">GA Desk</option>
                    <option value="GD">GD Desk</option>
                </select>
            </div>

            <div class="form-group wheelchair-select">
                <label for="wheelchair-options">Select Wheelchair Number:</label>
                <select id="wheelchair-options" name="wheelchair" required></select>
            </div>

            <!-- Security Deposit Fields -->


           <div class="form-section">
    <label>Security Deposit:</label>
    <div class="radio-group">
        <input type="radio" id="id-license" name="deposit-type" value="id-license" onclick="toggleSecurityDepositOptions()" required>
        <label for="id-license">ID and License</label>

        <input type="radio" id="currency" name="deposit-type" value="cash" onclick="toggleSecurityDepositOptions()">
        <label for="currency">Currency</label>

        <input type="radio" id="security" name="deposit-type" value="security" onclick="toggleSecurityDepositOptions()">
        <label for="security">Handed over to Security</label>
    </div>
</div>


            <div id="id-fields" class="form-group hidden">
                <label for="id-number">ID Number:</label>
                <input type="text" id="id-number" name="id-number">
            </div>

            <div id="cash-fields" class="form-group hidden">
                <label for="cash-amount">Cash Amount:</label>
                <input type="number" id="cash-amount" name="cash-amount">
            </div>

            <div id="handed-over-fields" class="form-group hidden">
                <label for="security-id">Security & Customer ID Number:</label>
                <input type="text" id="security-id" name="security-id">
            </div>

            <div class="form-group">
                <label for="last-date">Last Date:</label>
                <input type="date" id="last-date" name="last-date" class="medium-input" required>
            </div>

            <!-- CSA Name Dropdown -->
            <div class="form-group">
                <label for="csa-name">CSA Name:</label>
                <select id="csa-name" name="csa-name" required>
                    <option value="" disabled selected>Select CSA Name</option>
                    <option value="Marie">Marie</option>
                    <option value="Varun">Varun</option>
                    <option value="Allaine">Allaine</option>
                    <option value="Kaye">Kaye</option>
                    <option value="Iswary">Iswary</option>
                    <option value="Aqil">Aqil</option>
                    <option value="Kim">Kim</option>
                    <option value="Aahaan">Aahaan</option>
                    <option value="Wasan">Wasan</option>
                    <option value="Flora">Flora</option>
                    <option value="Abdelrahman">Abdelrahman</option>
                    <option value="April">April</option>
                    <option value="Amine">Amine</option>
                    <option value="Saber">Saber</option>
                    <option value="Sadaf">Sadaf</option>
                    <option value="Alameen">Alameen</option>
                    <option value="Anjum">Anjum</option>
                    <option value="Nourhan">Nourhan</option>
                    <option value="Yasmine">Yasmine</option>
                    <option value="Afrith">Afrith</option>
                    <option value="Alnoor">Alnoor</option>
                </select>
            </div>

            <button type="submit">Submit</button>
        </form>
    </div>
</body>
</html>
