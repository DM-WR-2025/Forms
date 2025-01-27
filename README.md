# Dragon Mart 1 & 2
<!DOCTYPE html>
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

        /* Mobile responsiveness */
        @media (max-width: 768px) {
            .container {
                width: 90%;
                padding: 15px;
            }

            h2 {
                font-size: 20px;
            }

            .medium-input, select {
                width: 100%;
            }

            .wheelchair-select select {
                width: 100%;
            }

            button {
                width: 100%;
                padding: 12px;
                font-size: 16px;
            }

            .form-group {
                margin-bottom: 15px;
            }

            label {
                font-size: 14px;
            }
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

        function updatePhoneCode() {
            var nationality = document.getElementById("nationality").value;
            var phoneField = document.getElementById("phone");

            var countryCodes = {
                "Bahrain": "+973",
                "Kuwait": "+965",
                "Oman": "+968",
                "Qatar": "+974",
                "Saudi Arabia": "+966",
                "United Arab Emirates": "+971",
                "USA": "+1",
                "Canada": "+1",
                "India": "+91",
                "Australia": "+61",
                "United Kingdom": "+44",
                "Germany": "+49",
                "France": "+33",
                "Japan": "+81",
                "China": "+86",
                "Brazil": "+55",
                "South Africa": "+27",
                "Russia": "+7",
                "Mexico": "+52",
                "Italy": "+39",
                "Spain": "+34",
                "Argentina": "+54",
                "Egypt": "+20",
                "Turkey": "+90",
                "Pakistan": "+92",
                "Singapore": "+65",
                "New Zealand": "+64",
                "Sudan": "+249"
            };

            if (nationality === "Other Country") {
                phoneField.placeholder = "Enter country code and phone number";
                phoneField.value = ""; // Clear the value
            } else if (countryCodes[nationality]) {
                phoneField.value = countryCodes[nationality]; // Pre-fill the country code
                phoneField.placeholder = countryCodes[nationality] + " - Phone Number";
            }
        }
    </script>
</head>
<body>
    <div class="container">
        <h2>Wheelchair Registration Form</h2>
        <form action="https://script.google.com/macros/s/AKfycbxVO23PuUc2S7DmmBdsJ5w2l-8aAfZOMPqw00iMJ4MHu7xnzgrrUuWE7MoAjV0WB43jJA/exec" method="POST" enctype="multipart/form-data" onsubmit="return confirmSubmission()">
            
            <div class="form-group">
                <label for="customer-name">Customer Name:</label>
                <input type="text" id="customer-name" name="customer-name" required class="medium-input">
            </div>

            <!-- Nationality Dropdown -->
            <div class="form-group">
                <label for="nationality">Nationality:</label>
                <select id="nationality" name="nationality" onchange="updatePhoneCode()" required class="medium-input">
                    <option value="" disabled selected>Select a nationality</option>
                    <option value="Bahrain">Bahrain</option>
                    <option value="Kuwait">Kuwait</option>
                    <option value="Oman">Oman</option>
                    <option value="Qatar">Qatar</option>
                    <option value="Saudi Arabia">Saudi Arabia</option>
                    <option value="United Arab Emirates">United Arab Emirates</option>
                    <option value="USA">USA</option>
                    <option value="Canada">Canada</option>
                    <option value="India">India</option>
                    <option value="Australia">Australia</option>
                    <option value="United Kingdom">United Kingdom</option>
                    <option value="Germany">Germany</option>
                    <option value="France">France</option>
                    <option value="Japan">Japan</option>
                    <option value="China">China</option>
                    <option value="Brazil">Brazil</option>
                    <option value="South Africa">South Africa</option>
                    <option value="Russia">Russia</option>
                    <option value="Mexico">Mexico</option>
                    <option value="Italy">Italy</option>
                    <option value="Spain">Spain</option>
                    <option value="Argentina">Argentina</option>
                    <option value="Egypt">Egypt</option>
                    <option value="Turkey">Turkey</option>
                    <option value="Pakistan">Pakistan</option>
                    <option value="Singapore">Singapore</option>
                    <option value="New Zealand">New Zealand</option>
                    <option value="Sudan">Sudan</option>
                    <option value="Other Country">Other Country</option>
                </select>
            </div>

            <!-- Phone Number Field -->
            <div class="form-group">
                <label for="phone">Phone Number:</label>
                <input type="tel" id="phone" name="phone" required class="medium-input">
            </div>

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

            <!-- Security Deposit Section -->
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
                <label for="security-id">Security & Customer ID Number:</label>
                <input type="text" id="security-id" name="security-id">
            </div>

            <div class="form-group">
                <label for="last-date">Last Date:</label>
                <input type="date" id="last-date" name="last-date" class="medium-input" required>
            </div>

            <div class="form-group">
                <label for="csa-name">CSA Name:</label>
                <select id="csa-name" name="csa-name" class="medium-input" required>
                    <option value="" disabled selected>Select a CSA Name</option>
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
                    <option value="Sadaf">Sadaf</option>
                    <option value="Saber">Saber</option>
                    <option value="Salma">Salma</option>
                    <option value="Alameen">Alameen</option>
                    <option value="Anjum">Anjum</option>
                    <option value="Nourhan">Nourhan</option>
                    <option value="Yasmine">Yasmine</option>
                    <option value="Afrith">Afrith</option>
                    <option value="Alnoor">Alnoor</option>
                    <option value="Teamleader">Team leader</option>
                </select>
            </div>

            <button type="submit">Submit</button>
        </form>
    </div>
    <div class="footer">
        <p>&copy; 2025 Wheelchair Registration System</p>
    </div>
</body>
</html>
