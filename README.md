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
        <img src="https://github.com/DM-WR-2025/Forms/blob/7d29aa5ee3f9a62d44f25957b864c8673632e0a9/DUBAI%20HOLDING%20LOGO.png" alt="Your Logo" width="150">
         <img src="https://github.com/DM-WR-2025/Forms/raw/416a4e06e8f80b074a18ab18543fd37267c1a755/dm%20-logo.png" alt="Your Logo" width="150">

        <h2>DM Wheelchair Registration Form</h2>
        <form action="https://script.google.com/macros/s/AKfycbzpej4RnNz5gLMdHGG-Wn9yMNaXiVw3JX-2W1nX6zlgwMBbNIyzUiXC8G7rQ_f6hy4R/exec" method="POST" enctype="multipart/form-data" onsubmit="return confirmSubmission()">
           
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
        <option value="Bahrain">Bahrain</option>
        <option value="Kuwait">Kuwait</option>
        <option value="Oman">Oman</option>
        <option value="Qatar">Qatar</option>
        <option value="Saudi Arabia">Saudi Arabia</option>
        <option value="United Arab Emirates">United Arab Emirates</option>

        <!-- Other Countries (A to Z) -->
        <option value="Afghanistan">Afghanistan</option>
        <option value="Albania">Albania</option>
        <option value="Algeria">Algeria</option>
        <option value="Andorra">Andorra</option>
        <option value="Angola">Angola</option>
        <option value="Antigua and Barbuda">Antigua and Barbuda</option>
        <option value="Argentina">Argentina</option>
        <option value="Armenia">Armenia</option>
        <option value="Australia">Australia</option>
        <option value="Austria">Austria</option>
        <option value="Azerbaijan">Azerbaijan</option>
        <option value="Bahamas">Bahamas</option>
        <option value="Bangladesh">Bangladesh</option>
        <option value="Barbados">Barbados</option>
        <option value="Belarus">Belarus</option>
        <option value="Belgium">Belgium</option>
        <option value="Belize">Belize</option>
        <option value="Benin">Benin</option>
        <option value="Bhutan">Bhutan</option>
        <option value="Bolivia">Bolivia</option>
        <option value="Bosnia and Herzegovina">Bosnia and Herzegovina</option>
        <option value="Botswana">Botswana</option>
        <option value="Brazil">Brazil</option>
        <option value="Brunei">Brunei</option>
        <option value="Bulgaria">Bulgaria</option>
        <option value="Burkina Faso">Burkina Faso</option>
        <option value="Burundi">Burundi</option>
        <option value="Cabo Verde">Cabo Verde</option>
        <option value="Cambodia">Cambodia</option>
        <option value="Cameroon">Cameroon</option>
        <option value="Canada">Canada</option>
        <option value="Central African Republic">Central African Republic</option>
        <option value="Chad">Chad</option>
        <option value="Chile">Chile</option>
        <option value="China">China</option>
        <option value="Colombia">Colombia</option>
        <option value="Comoros">Comoros</option>
        <option value="Congo">Congo</option>
        <option value="Congo, Democratic Republic of the">Congo, Democratic Republic of the</option>
        <option value="Costa Rica">Costa Rica</option>
        <option value="Croatia">Croatia</option>
        <option value="Cuba">Cuba</option>
        <option value="Cyprus">Cyprus</option>
        <option value="Czech Republic">Czech Republic</option>
        <option value="Denmark">Denmark</option>
        <option value="Djibouti">Djibouti</option>
        <option value="Dominica">Dominica</option>
        <option value="Dominican Republic">Dominican Republic</option>
        <option value="Ecuador">Ecuador</option>
        <option value="Egypt">Egypt</option>
        <option value="El Salvador">El Salvador</option>
        <option value="Equatorial Guinea">Equatorial Guinea</option>
        <option value="Eritrea">Eritrea</option>
        <option value="Estonia">Estonia</option>
        <option value="Eswatini">Eswatini</option>
        <option value="Ethiopia">Ethiopia</option>
        <option value="Fiji">Fiji</option>
        <option value="Finland">Finland</option>
        <option value="France">France</option>
        <option value="Gabon">Gabon</option>
        <option value="Gambia">Gambia</option>
        <option value="Georgia">Georgia</option>
        <option value="Germany">Germany</option>
        <option value="Ghana">Ghana</option>
        <option value="Greece">Greece</option>
        <option value="Grenada">Grenada</option>
        <option value="Guatemala">Guatemala</option>
        <option value="Guinea">Guinea</option>
        <option value="Guinea-Bissau">Guinea-Bissau</option>
        <option value="Guyana">Guyana</option>
        <option value="Haiti">Haiti</option>
        <option value="Honduras">Honduras</option>
        <option value="Hungary">Hungary</option>
        <option value="Iceland">Iceland</option>
        <option value="India">India</option>
        <option value="Indonesia">Indonesia</option>
        <option value="Iran">Iran</option>
        <option value="Iraq">Iraq</option>
        <option value="Ireland">Ireland</option>
        <option value="Israel">Israel</option>
        <option value="Italy">Italy</option>
        <option value="Jamaica">Jamaica</option>
        <option value="Japan">Japan</option>
        <option value="Jordan">Jordan</option>
        <option value="Kazakhstan">Kazakhstan</option>
        <option value="Kenya">Kenya</option>
        <option value="Kiribati">Kiribati</option>
        <option value="Korea, North">Korea, North</option>
        <option value="Korea, South">Korea, South</option>
        <option value="Kyrgyzstan">Kyrgyzstan</option>
        <option value="Laos">Laos</option>
        <option value="Latvia">Latvia</option>
        <option value="Lebanon">Lebanon</option>
        <option value="Lesotho">Lesotho</option>
        <option value="Liberia">Liberia</option>
        <option value="Libya">Libya</option>
        <option value="Liechtenstein">Liechtenstein</option>
        <option value="Lithuania">Lithuania</option>
        <option value="Luxembourg">Luxembourg</option>
        <option value="Madagascar">Madagascar</option>
        <option value="Malawi">Malawi</option>
        <option value="Malaysia">Malaysia</option>
        <option value="Maldives">Maldives</option>
        <option value="Mali">Mali</option>
        <option value="Malta">Malta</option>
        <option value="Marshall Islands">Marshall Islands</option>
        <option value="Mauritania">Mauritania</option>
        <option value="Mauritius">Mauritius</option>
        <option value="Mexico">Mexico</option>
        <option value="Micronesia">Micronesia</option>
        <option value="Moldova">Moldova</option>
        <option value="Monaco">Monaco</option>
        <option value="Mongolia">Mongolia</option>
        <option value="Montenegro">Montenegro</option>
        <option value="Morocco">Morocco</option>
        <option value="Mozambique">Mozambique</option>
        <option value="Myanmar">Myanmar</option>
        <option value="Namibia">Namibia</option>
        <option value="Nauru">Nauru</option>
        <option value="Nepal">Nepal</option>
        <option value="Netherlands">Netherlands</option>
        <option value="New Zealand">New Zealand</option>
        <option value="Nicaragua">Nicaragua</option>
        <option value="Niger">Niger</option>
        <option value="Nigeria">Nigeria</option>
        <option value="North Macedonia">North Macedonia</option>
        <option value="Norway">Norway</option>
        <option value="Pakistan">Pakistan</option>
        <option value="Palau">Palau</option>
        <option value="Panama">Panama</option>
        <option value="Papua New Guinea">Papua New Guinea</option>
        <option value="Paraguay">Paraguay</option>
        <option value="Peru">Peru</option>
        <option value="Philippines">Philippines</option>
        <option value="Poland">Poland</option>
        <option value="Portugal">Portugal</option>
        <option value="Romania">Romania</option>
        <option value="Russia">Russia</option>
        <option value="Rwanda">Rwanda</option>
        <option value="Saint Kitts and Nevis">Saint Kitts and Nevis</option>
        <option value="Saint Lucia">Saint Lucia</option>
        <option value="Saint Vincent and the Grenadines">Saint Vincent and the Grenadines</option>
        <option value="Samoa">Samoa</option>
        <option value="San Marino">San Marino</option>
        <option value="Sao Tome and Principe">Sao Tome and Principe</option>
        <option value="Senegal">Senegal</option>
        <option value="Serbia">Serbia</option>
        <option value="Seychelles">Seychelles</option>
        <option value="Sierra Leone">Sierra Leone</option>
        <option value="Singapore">Singapore</option>
        <option value="Slovakia">Slovakia</option>
        <option value="Slovenia">Slovenia</option>
        <option value="Solomon Islands">Solomon Islands</option>
        <option value="Somalia">Somalia</option>
        <option value="South Africa">South Africa</option>
        <option value="South Korea">South Korea</option>
        <option value="South Sudan">South Sudan</option>
        <option value="Spain">Spain</option>
        <option value="Sri Lanka">Sri Lanka</option>
        <option value="Sudan">Sudan</option>
        <option value="Suriname">Suriname</option>
        <option value="Sweden">Sweden</option>
        <option value="Switzerland">Switzerland</option>
        <option value="Syria">Syria</option>
        <option value="Taiwan">Taiwan</option>
        <option value="Tajikistan">Tajikistan</option>
        <option value="Tanzania">Tanzania</option>
        <option value="Thailand">Thailand</option>
        <option value="Togo">Togo</option>
        <option value="Tonga">Tonga</option>
        <option value="Trinidad and Tobago">Trinidad and Tobago</option>
        <option value="Tunisia">Tunisia</option>
        <option value="Turkey">Turkey</option>
        <option value="Turkmenistan">Turkmenistan</option>
        <option value="Tuvalu">Tuvalu</option>
        <option value="Uganda">Uganda</option>
        <option value="Ukraine">Ukraine</option>
        <option value="United Kingdom">United Kingdom</option>
        <option value="United States">United States</option>
        <option value="Uruguay">Uruguay</option>
        <option value="Uzbekistan">Uzbekistan</option>
        <option value="Vanuatu">Vanuatu</option>
        <option value="Vatican City">Vatican City</option>
        <option value="Venezuela">Venezuela</option>
        <option value="Vietnam">Vietnam</option>
        <option value="Yemen">Yemen</option>
        <option value="Zambia">Zambia</option>
        <option value="Zimbabwe">Zimbabwe</option>
    </select>
</div>

<div class="form-group">
    <label for="customer-type">Customer Type:</label>
    <div class="radio-group">
        <label><input type="radio" name="customer-type" value="Resident" required> Resident</label>
        <label><input type="radio" name="customer-type" value="Visitor" required> Visitor</label>
    </div>
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

  <label for="currency-type" class="currency-label">Currency:</label>
  <select id="currency-type" name="currency-type" class="currency-select">
    <option value="usd">USD (Dollar)</option>
    <option value="aed">AED (Dirham)</option>
    <option value="sar">SAR (Riyal)</option>
    <option value="bhd">BHD (Dinar)</option>
    <option value="kwd">KWD (Dinar)</option>
    <option value="omr">OMR (Rial)</option>
    <option value="qat">QAR (Riyal)</option>
    <option value="jod">JOD (Jordanian Dinar)</option>
    <option value="eur">EUR (Euro)</option>
    <option value="other">Other</option>
  </select>
</div>

<div id="handed-over-fields" class="form-group hidden">
  <div class="two-fields">
    <div class="field-container">
      <label for="security-id">Security ID:</label>
      <input type="text" id="security-id" name="security-id">
    </div>
    <div class="field-container">
      <label for="customer-id">Customer ID:</label>
      <input type="text" id="customer-id" name="customer-id">
    </div>
  </div>
</div>


<div class="form-group">
    <label for="last-date">Last Date:</label>
    <input type="date" id="last-date" name="last-date" class="medium-input" required>
</div>

<script>
    function toggleSecurityDepositOptions() {
      const idFields = document.getElementById('id-fields');
      const cashFields = document.getElementById('cash-fields');
      const handedOverFields = document.getElementById('handed-over-fields');

      const idNumber = document.getElementById('id-number');
      const cashAmount = document.getElementById('cash-amount');
      const currencyType = document.getElementById('currency-type');
      const securityId = document.getElementById('security-id');
      const customerId = document.getElementById('customer-id');

      const selectedType = document.querySelector('input[name="deposit-type"]:checked')?.value;

      // Hide and disable all first
      idFields.classList.add('hidden');
      idNumber.disabled = true;

      cashFields.classList.add('hidden');
      cashAmount.disabled = true;
      currencyType.disabled = true;

      handedOverFields.classList.add('hidden');
      securityId.disabled = true;
      customerId.disabled = true;

      // Show and enable based on selection
      if (selectedType === 'id-license') {
        idFields.classList.remove('hidden');
        idNumber.disabled = false;
      } else if (selectedType === 'cash') {
        cashFields.classList.remove('hidden');
        cashAmount.disabled = false;
        currencyType.disabled = false;
      } else if (selectedType === 'security') {
        handedOverFields.classList.remove('hidden');
        securityId.disabled = false;
        customerId.disabled = false;
      }
    }
  </script>

<label for="return_location">Return Location:</label>
  <select id="return_location" name="return_location" required>
    <option value="">-- Select Return Desk --</option>
    <option value="BA Desk">BA Desk</option>
    <option value="F Desk">F Desk</option>
    <option value="H Desk">H Desk</option>
    <option value="GA Desk">GA Desk</option>
    <option value="GD Desk">GD Desk</option>
    <option value="Security Office">Security Office</option>
  </select>

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
