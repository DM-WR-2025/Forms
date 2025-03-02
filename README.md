<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wheelchair Registration Form</title>
    <style>
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
    </style>
    <script>
        function showWheelchairOptions() {
            var desk = document.getElementById("desk").value;
            var wheelchairOptions = document.getElementById("wheelchair-options");
            wheelchairOptions.innerHTML = ''; // Clear current wheelchair options
            var startNumber = 0;

            if (desk == 'BA') {
                startNumber = 1;
            } else if (desk == 'F') {
                startNumber = 4;
            } else if (desk == 'H') {
                startNumber = 7;
            } else if (desk == 'GA') {
                startNumber = 10;
            } else if (desk == 'GD') {
                startNumber = 12;
            }

            var maxWheelchairs = (desk == 'GA' || desk == 'GD') ? 2 : 3;

            for (var i = startNumber; i < startNumber + maxWheelchairs; i++) {
                wheelchairOptions.innerHTML += `<option value="${i}">${i}</option>`;
            }
        }

        function toggleSecurityDepositOptions() {
            var depositType = document.querySelector('input[name="deposit-type"]:checked').value;
            var idFields = document.getElementById("id-fields");
            var cashFields = document.getElementById("cash-fields");
            var handedOverFields = document.getElementById("handed-over-fields");

            if (depositType == 'id-license') {
                idFields.classList.remove('hidden');
                cashFields.classList.add('hidden');
                handedOverFields.classList.add('hidden');
            } else if (depositType == 'cash') {
                idFields.classList.add('hidden');
                cashFields.classList.remove('hidden');
                handedOverFields.classList.add('hidden');
            } else if (depositType == 'security') {
                idFields.classList.add('hidden');
                cashFields.classList.add('hidden');
                handedOverFields.classList.remove('hidden');
            }
        }

        function confirmSubmission() {
            alert("Form successfully submitted!");
            return true;
        }
    </script>
</head>
<body>
    <div class="container">
        <h2>Wheelchair Registration Form</h2>
        <form action="https://script.google.com/macros/s/AKfycbxnPftPwSE9lp1wo9Gmj_YSlEDVtnt60SmkWyomki-olJfxDUCbsYe15-UPdbWcvty0LQ/exec" method="POST" enctype="multipart/form-data" onsubmit="return confirmSubmission()">
            
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
                    <option value="United States">United States</option>
                    <option value="Canada">Canada</option>
                    <option value="United Kingdom">United Kingdom</option>
                    <option value="India">India</option>
                    <option value="Australia">Australia</option>
                    <option value="Germany">Germany</option>
                    <option value="France">France</option>
                    <option value="Spain">Spain</option>
                    <option value="Italy">Italy</option>
                    <option value="China">China</option>
                    <option value="Japan">Japan</option>
                    <option value="Brazil">Brazil</option>
                    <option value="Mexico">Mexico</option>
                    <option value="Russia">Russia</option>
                    <option value="South Africa">South Africa</option>
                    <option value="Argentina">Argentina</option>
                    <option value="Nigeria">Nigeria</option>
                    <option value="Egypt">Egypt</option>
                    <option value="South Korea">South Korea</option>
                    <option value="Singapore">Singapore</option>
                    <option value="Philippines">Philippines</option>
                    <option value="Thailand">Thailand</option>
                    <option value="Netherlands">Netherlands</option>
                    <option value="Sweden">Sweden</option>
                    <option value="Finland">Finland</option>
                    <option value="Norway">Norway</option>
                    <option value="Denmark">Denmark</option>
                    <option value="Poland">Poland</option>
                    <option value="Greece">Greece</option>
                    <option value="Turkey">Turkey</option>
                    <option value="Saudi Arabia">Saudi Arabia</option>
                    <option value="United Arab Emirates">United Arab Emirates</option>
                    <option value="Malaysia">Malaysia</option>
                    <option value="Indonesia">Indonesia</option>
                    <option value="Vietnam">Vietnam</option>
                    <option value="Pakistan">Pakistan</option>
                    <option value="Bangladesh">Bangladesh</option>
                    <option value="Cambodia">Cambodia</option>
                    <option value="Sri Lanka">Sri Lanka</option>
                    <option value="Kenya">Kenya</option>
                    <option value="Uganda">Uganda</option>
                    <option value="Ethiopia">Ethiopia</option>
                    <option value="Tanzania">Tanzania</option>
                    <option value="Malawi">Malawi</option>
                    <option value="Zimbabwe">Zimbabwe</option>
                    <option value="Peru">Peru</option>
                    <option value="Chile">Chile</option>
                    <option value="Colombia">Colombia</option>
                    <option value="Venezuela">Venezuela</option>
                    <option value="Cuba">Cuba</option>
                    <option value="Ecuador">Ecuador</option>
                    <option value="Paraguay">Paraguay</option>
                    <option value="Bolivia">Bolivia</option>
                    <option value="Suriname">Suriname</option>
                    <option value="Guyana">Guyana</option>
                </select>
            </div>

            <!-- Phone Number Next -->
            <div class="form-group">
                <label for="phone">Phone Number:</label>
                <input type="tel" id="phone" name="phone" required class="medium-input">
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

            <div class="form-section">
                <label>Security Deposit:</label>
                <div class="radio-group">
                    <input type="radio" id="id-license" name="deposit-type" value="id-license" onclick="toggleSecurityDepositOptions()" required>
                    <label for="id-license">ID and License</label>

                    <input type="radio" id="cash" name="deposit-type" value="cash" onclick="toggleSecurityDepositOptions()">
                    <label for="cash">Cash</label>

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
                <label for="security-id">Security&Customer ID Number:</label>
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
