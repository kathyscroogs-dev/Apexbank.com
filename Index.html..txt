<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apex Bank of Texas | Secure Login</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f7f6;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        /* Login Container */
        .container {
            background: white;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            width: 100%;
            max-width: 450px;
            text-align: center;
        }

        .header {
            color: #004a99;
            border-bottom: 2px solid #ce1126; /* Texas Red */
            margin-bottom: 1.5rem;
            padding-bottom: 0.5rem;
        }

        input {
            width: 90%;
            padding: 12px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            width: 95%;
            padding: 12px;
            background-color: #004a99;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
        }

        button:hover {
            background-color: #003366;
        }

        /* Dashboard Styles (Hidden by default) */
        #dashboard {
            display: none;
            max-width: 800px;
            text-align: left;
        }

        .balance-card {
            background: #004a99;
            color: white;
            padding: 1.5rem;
            border-radius: 8px;
            margin-bottom: 2rem;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }

        th, td {
            padding: 12px;
            border-bottom: 1px solid #ddd;
            text-align: left;
        }

        th { background-color: #f8f9fa; }

        .credit { color: green; font-weight: bold; }
        .debit { color: #ce1126; font-weight: bold; }
    </style>
</head>
<body>

    <div id="login-screen" class="container">
        <h2 class="header">APEX BANK OF TEXAS</h2>
        <p>Secure Online Access</p>
        <input type="text" id="username" placeholder="User ID (m_bradley_tx)">
        <input type="password" id="pin" placeholder="4-Digit PIN (9901)">
        <button onclick="handleLogin()">Login to Secure Portal</button>
        <p id="error-msg" style="color: red; display: none; margin-top: 10px;">Invalid Credentials</p>
    </div>

    <div id="dashboard" class="container">
        <h2 class="header">APEX BANK OF TEXAS</h2>
        <div class="balance-card">
            <p>Welcome, <strong>Mark Bradley</strong></p>
            <h3>Savings Balance: $1,250,003.00</h3>
        </div>

        <h4>Recent Transactions</h4>
        <table id="tx-table">
            <thead>
                <tr>
                    <th>Date</th>
                    <th>Description</th>
                    <th>Amount</th>
                </tr>
            </thead>
            <tbody id="tx-body">
                </tbody>
        </table>
    </div>

    <script>
        const transactions = [
            { date: "2026-02-01", desc: "Direct Deposit-Payroll", amt: "+$25,000.00", type: "credit" },
            { date: "2026-02-01", desc: "Texas Property Tax", amt: "-$18,400.00", type: "debit" },
            { date: "2026-02-02", desc: "Chevron Fuel Austin", amt: "-$89.50", type: "debit" },
            { date: "2026-02-03", desc: "Tech Dividends", amt: "+$4,250.00", type: "credit" },
            { date: "2026-02-04", desc: "Lone Star Steakhouse", amt: "-$312.00", type: "debit" },
            { date: "2026-02-05", desc: "Monthly Interest Inc", amt: "+$1,102.44", type: "credit" },
            { date: "2026-02-06", desc: "Austin Equine Center", amt: "-$2,500.00", type: "debit" },
            { date: "2026-02-07", desc: "Wire Transfer In", amt: "+$50,000.00", type: "credit" },
            { date: "2026-02-07", desc: "Zelle: To Sarah Bradley", amt: "-$1,200.00", type: "debit" },
            { date: "2026-02-08", desc: "Zelle: From J. Miller", amt: "+$450.00", type: "credit" },
            { date: "2026-02-08", desc: "Zelle: To Lone Star Land", amt: "-$3,500.00", type: "debit" },
            { date: "2026-02-08", desc: "Zelle: To Austin Valet", amt: "-$150.00", type: "debit" },
            { date: "2026-02-08", desc: "Zelle: From Rental Unit B", amt: "+$2,100.00", type: "credit" }
        ];

        function handleLogin() {
            const user = document.getElementById('username').value;
            const pin = document.getElementById('pin').value;

            // Check against simulated credentials
            if (user === "m_bradley_tx" && pin === "9901") {
                document.getElementById('login-screen').style.display = 'none';
                document.getElementById('dashboard').style.display = 'block';
                loadTransactions();
            } else {
                document.getElementById('error-msg').style.display = 'block';
            }
        }

        function loadTransactions() {
            const tableBody = document.getElementById('tx-body');
            transactions.forEach(tx => {
                const row = `<tr>
                    <td>${tx.date}</td>
                    <td>${tx.desc}</td>
                    <td class="${tx.type}">${tx.amt}</td>
                </tr>`;
                tableBody.innerHTML += row;
            });
        }
    </script>
</body>
</html>
