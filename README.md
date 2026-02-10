# noe-taieb.github.io
index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Structured Products Allocation Tool</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', sans-serif;
            background-color: #0f0f0f;
            color: #e0e0e0;
            min-height: 100vh;
            padding: 40px 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            max-width: 580px;
            width: 100%;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding-bottom: 24px;
            border-bottom: 1px solid #232323;
        }

        .header h1 {
            font-size: 26px;
            font-weight: 500;
            color: #ffffff;
            letter-spacing: -0.5px;
            margin-bottom: 8px;
        }

        .header .subtitle {
            font-size: 13px;
            color: #888888;
            font-weight: 400;
        }

        .investment-panel {
            background: linear-gradient(135deg, #1a1a1a 0%, #151515 100%);
            border: 1px solid #232323;
            border-radius: 8px;
            padding: 28px;
            text-align: center;
            margin-bottom: 36px;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
        }

        .investment-label {
            font-size: 11px;
            color: #888888;
            text-transform: uppercase;
            letter-spacing: 1.2px;
            margin-bottom: 10px;
            font-weight: 500;
        }

        .investment-amount {
            font-size: 38px;
            font-weight: 300;
            color: #00d2d3;
            font-variant-numeric: tabular-nums;
            letter-spacing: -1px;
        }

        .products-container {
            margin-bottom: 36px;
        }

        .product-card {
            background-color: #1a1a1a;
            border: 1px solid #232323;
            border-radius: 8px;
            padding: 24px;
            margin-bottom: 18px;
            transition: all 0.25s ease;
        }

        .product-card:hover {
            border-color: #2a2a2a;
            background-color: #1c1c1c;
        }

        .product-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 18px;
        }

        .product-title {
            font-size: 17px;
            font-weight: 500;
            color: #ffffff;
            letter-spacing: -0.2px;
        }

        .product-allocation {
            font-size: 19px;
            font-weight: 400;
            color: #00d2d3;
            font-variant-numeric: tabular-nums;
        }

        .slider-wrapper {
            margin-top: 16px;
        }

        input[type="range"] {
            width: 100%;
            height: 3px;
            border-radius: 2px;
            background: #2a2a2a;
            outline: none;
            -webkit-appearance: none;
            cursor: pointer;
        }

        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            background: #00d2d3;
            cursor: pointer;
            box-shadow: 0 2px 8px rgba(0, 210, 211, 0.4);
            transition: all 0.2s ease;
        }

        input[type="range"]::-webkit-slider-thumb:hover {
            transform: scale(1.15);
            box-shadow: 0 3px 12px rgba(0, 210, 211, 0.6);
        }

        input[type="range"]::-moz-range-thumb {
            width: 18px;
            height: 18px;
            border-radius: 50%;
            background: #00d2d3;
            cursor: pointer;
            border: none;
            box-shadow: 0 2px 8px rgba(0, 210, 211, 0.4);
        }

        input[type="range"]:disabled {
            opacity: 0.4;
            cursor: not-allowed;
        }

        input[type="range"]:disabled::-webkit-slider-thumb {
            background: #555555;
            cursor: not-allowed;
        }

        input[type="range"]:disabled::-moz-range-thumb {
            background: #555555;
            cursor: not-allowed;
        }

        .action-button {
            width: 100%;
            padding: 17px;
            font-size: 14px;
            font-weight: 500;
            color: #0f0f0f;
            background: linear-gradient(135deg, #00d2d3 0%, #00b8b9 100%);
            border: none;
            border-radius: 8px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1.2px;
            transition: all 0.25s ease;
            box-shadow: 0 4px 16px rgba(0, 210, 211, 0.25);
        }

        .action-button:hover {
            transform: translateY(-1px);
            box-shadow: 0 6px 20px rgba(0, 210, 211, 0.35);
        }

        .action-button:active {
            transform: translateY(0);
        }

        /* Results Screen */
        .results-screen {
            display: none;
        }

        .results-header {
            text-align: center;
            margin-bottom: 32px;
            padding-bottom: 20px;
            border-bottom: 1px solid #232323;
        }

        .results-header h2 {
            font-size: 24px;
            font-weight: 500;
            color: #ffffff;
            margin-bottom: 10px;
            letter-spacing: -0.5px;
        }

        .strategy-assessment {
            background: linear-gradient(135deg, #1a1a1a 0%, #151515 100%);
            border-radius: 8px;
            padding: 24px;
            margin-bottom: 28px;
            text-align: center;
            border: 1px solid #232323;
        }

        .assessment-label {
            font-size: 10px;
            color: #888888;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 12px;
            font-weight: 500;
        }

        .assessment-title {
            font-size: 18px;
            font-weight: 500;
            line-height: 1.5;
        }

        .assessment-expert {
            color: #00d2d3;
        }

        .assessment-balanced {
            color: #ffa500;
        }

        .assessment-inefficient {
            color: #ff2e63;
        }

        .metrics-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 14px;
            margin-bottom: 28px;
        }

        .metric-box {
            background-color: #1a1a1a;
            border: 1px solid #232323;
            border-radius: 8px;
            padding: 20px;
        }

        .metric-label {
            font-size: 10px;
            color: #888888;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 10px;
            font-weight: 500;
        }

        .metric-value {
            font-size: 24px;
            font-weight: 400;
            color: #ffffff;
            font-variant-numeric: tabular-nums;
        }

        .metric-value.gain {
            color: #00d2d3;
        }

        .metric-value.loss {
            color: #ff2e63;
        }

        .metric-value.warning {
            color: #ffa500;
        }

        .performance-breakdown {
            background-color: #1a1a1a;
            border: 1px solid #232323;
            border-radius: 8px;
            padding: 24px;
            margin-bottom: 24px;
        }

        .breakdown-header {
            font-size: 11px;
            color: #888888;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 18px;
            font-weight: 500;
        }

        .breakdown-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 14px 0;
            border-bottom: 1px solid #232323;
            font-size: 14px;
        }

        .breakdown-row:last-child {
            border-bottom: none;
            padding-bottom: 0;
        }

        .breakdown-product {
            color: #aaaaaa;
            font-weight: 400;
        }

        .breakdown-flow {
            color: #ffffff;
            font-weight: 400;
            font-variant-numeric: tabular-nums;
        }

        .volatility-disclosure {
            background-color: #1a1a1a;
            border: 1px solid #232323;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 24px;
        }

        .volatility-header {
            font-size: 11px;
            color: #888888;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 14px;
            font-weight: 500;
        }

        .volatility-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            font-size: 13px;
        }

        .volatility-name {
            color: #aaaaaa;
        }

        .volatility-value {
            color: #ffa500;
            font-weight: 500;
        }

        .reset-button {
            width: 100%;
            padding: 15px;
            font-size: 13px;
            font-weight: 500;
            color: #00d2d3;
            background-color: transparent;
            border: 1px solid #00d2d3;
            border-radius: 8px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1.2px;
            transition: all 0.25s ease;
        }

        .reset-button:hover {
            background-color: rgba(0, 210, 211, 0.1);
            border-color: #00b8b9;
        }

        @media (max-width: 480px) {
            body {
                padding: 24px 16px;
            }

            .header h1 {
                font-size: 22px;
            }

            .investment-amount {
                font-size: 32px;
            }

            .metrics-grid {
                grid-template-columns: 1fr;
            }

            .product-title {
                font-size: 16px;
            }

            .product-allocation {
                font-size: 17px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Allocation Screen -->
        <div id="allocationScreen">
            <div class="header">
                <h1>Structured Products Allocation Tool</h1>
                <div class="subtitle">Boeing (BA) Investment Scenario: 3-Year Period</div>
            </div>

            <div class="investment-panel">
                <div class="investment-label">Available Capital</div>
                <div class="investment-amount" id="totalCapital">$100,000</div>
            </div>

            <div class="products-container">
                <div class="product-card">
                    <div class="product-header">
                        <div class="product-title">Supertracker</div>
                        <div class="product-allocation" id="alloc1">$0</div>
                    </div>
                    <div class="slider-wrapper">
                        <input type="range" id="slider1" min="0" max="100000" value="0" step="1000">
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-header">
                        <div class="product-title">Reverse Convertible</div>
                        <div class="product-allocation" id="alloc2">$0</div>
                    </div>
                    <div class="slider-wrapper">
                        <input type="range" id="slider2" min="0" max="100000" value="0" step="1000">
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-header">
                        <div class="product-title">Capital Guaranteed</div>
                        <div class="product-allocation" id="alloc3">$100,000</div>
                    </div>
                    <div class="slider-wrapper">
                        <input type="range" id="slider3" min="0" max="100000" value="100000" step="1000" disabled>
                    </div>
                </div>
            </div>

            <button class="action-button" onclick="calculateResults()">Analyze Portfolio</button>
        </div>

        <!-- Results Screen -->
        <div id="resultsScreen" class="results-screen">
            <div class="results-header">
                <h2>Portfolio Performance Report</h2>
                <div class="subtitle">3-Year Investment Analysis</div>
            </div>

            <div class="strategy-assessment">
                <div class="assessment-label">Strategy Classification</div>
                <div class="assessment-title" id="strategyTitle"></div>
            </div>

            <div class="metrics-grid">
                <div class="metric-box">
                    <div class="metric-label">Initial Capital</div>
                    <div class="metric-value">$100,000</div>
                </div>

                <div class="metric-box">
                    <div class="metric-label">Final Capital</div>
                    <div class="metric-value" id="finalCapital"></div>
                </div>

                <div class="metric-box">
                    <div class="metric-label">Total Return</div>
                    <div class="metric-value" id="totalReturn"></div>
                </div>

                <div class="metric-box">
                    <div class="metric-label">Portfolio Volatility</div>
                    <div class="metric-value warning" id="portfolioVol"></div>
                </div>

                <div class="metric-box">
                    <div class="metric-label">Sharpe Ratio</div>
                    <div class="metric-value" id="sharpeRatio"></div>
                </div>

                <div class="metric-box">
                    <div class="metric-label">Risk Classification</div>
                    <div class="metric-value" id="riskClass" style="font-size: 16px;"></div>
                </div>
            </div>

            <div class="volatility-disclosure">
                <div class="volatility-header">Product Risk Profiles (Revealed)</div>
                <div class="volatility-item">
                    <span class="volatility-name">Supertracker</span>
                    <span class="volatility-value">40% volatility</span>
                </div>
                <div class="volatility-item">
                    <span class="volatility-name">Reverse Convertible</span>
                    <span class="volatility-value">25% volatility</span>
                </div>
                <div class="volatility-item">
                    <span class="volatility-name">Capital Guaranteed</span>
                    <span class="volatility-value">1% volatility</span>
                </div>
            </div>

            <div class="performance-breakdown">
                <div class="breakdown-header">Product Performance Detail</div>
                <div class="breakdown-row">
                    <span class="breakdown-product">Supertracker</span>
                    <span class="breakdown-flow" id="flow1"></span>
                </div>
                <div class="breakdown-row">
                    <span class="breakdown-product">Reverse Convertible</span>
                    <span class="breakdown-flow" id="flow2"></span>
                </div>
                <div class="breakdown-row">
                    <span class="breakdown-product">Capital Guaranteed</span>
                    <span class="breakdown-flow" id="flow3"></span>
                </div>
            </div>

            <button class="reset-button" onclick="resetAllocation()">New Allocation</button>
        </div>
    </div>

    <script>
        // Portfolio state
        let portfolio = {
            product1: 0,
            product2: 0,
            product3: 100000
        };

        const TOTAL_CAPITAL = 100000;

        // Boeing V-Shape Recovery Scenario
        // Stock: Crashed 60% in Year 2, but recovered to finish +3%
        const MULTIPLIERS = {
            supertracker: 1.045,     // 1.5x leverage × 3% = 4.5% gain
            reverseConv: 1.24,       // Capital returned + 3 years × 8% coupon = 24% gain
            capitalGuar: 1.024       // 80% participation × 3% = 2.4% gain
        };

        // Hidden volatility scores (revealed after calculation)
        const VOLATILITIES = {
            supertracker: 0.40,      // 40% - very turbulent
            reverseConv: 0.25,       // 25% - scary mid-term
            capitalGuar: 0.01        // 1% - stable
        };

        // DOM elements
        const slider1 = document.getElementById('slider1');
        const slider2 = document.getElementById('slider2');
        const slider3 = document.getElementById('slider3');

        const alloc1 = document.getElementById('alloc1');
        const alloc2 = document.getElementById('alloc2');
        const alloc3 = document.getElementById('alloc3');

        // Event listeners
        slider1.addEventListener('input', updatePortfolio);
        slider2.addEventListener('input', updatePortfolio);

        function updatePortfolio() {
            portfolio.product1 = parseInt(slider1.value);
            portfolio.product2 = parseInt(slider2.value);

            // Auto-balance third product
            portfolio.product3 = TOTAL_CAPITAL - portfolio.product1 - portfolio.product2;

            // Prevent negative allocations
            if (portfolio.product3 < 0) {
                portfolio.product3 = 0;

                if (slider1.value !== slider1.dataset.lastValue) {
                    portfolio.product1 = TOTAL_CAPITAL - portfolio.product2;
                    slider1.value = portfolio.product1;
                } else {
                    portfolio.product2 = TOTAL_CAPITAL - portfolio.product1;
                    slider2.value = portfolio.product2;
                }
            }

            slider1.dataset.lastValue = slider1.value;
            slider2.dataset.lastValue = slider2.value;
            slider3.value = portfolio.product3;

            // Update UI
            alloc1.textContent = '$' + portfolio.product1.toLocaleString();
            alloc2.textContent = '$' + portfolio.product2.toLocaleString();
            alloc3.textContent = '$' + portfolio.product3.toLocaleString();
        }

        function calculateResults() {
            // Calculate final capital
            const finalCapital = 
                (portfolio.product1 * MULTIPLIERS.supertracker) +
                (portfolio.product2 * MULTIPLIERS.reverseConv) +
                (portfolio.product3 * MULTIPLIERS.capitalGuar);

            // Calculate total return percentage
            const totalReturn = ((finalCapital - TOTAL_CAPITAL) / TOTAL_CAPITAL) * 100;

            // Calculate allocation weights
            const w1 = portfolio.product1 / TOTAL_CAPITAL;
            const w2 = portfolio.product2 / TOTAL_CAPITAL;
            const w3 = portfolio.product3 / TOTAL_CAPITAL;

            // Calculate portfolio volatility
            const portfolioVol = Math.sqrt(
                Math.pow(w1 * VOLATILITIES.supertracker, 2) +
                Math.pow(w2 * VOLATILITIES.reverseConv, 2) +
                Math.pow(w3 * VOLATILITIES.capitalGuar, 2)
            ) * 100;

            // Calculate Sharpe Ratio
            let sharpeRatio;
            if (portfolioVol < 0.01) {
                sharpeRatio = 0;
            } else {
                sharpeRatio = totalReturn / portfolioVol;
            }

            // Determine strategy classification
            const strategy = classifyStrategy(sharpeRatio);

            // Display results
            showResults(finalCapital, totalReturn, portfolioVol, sharpeRatio, strategy);
        }

        function classifyStrategy(sharpe) {
            if (sharpe > 1.2) {
                return {
                    title: 'Strategy: Expert Optimization (High Yield / Managed Risk)',
                    className: 'assessment-expert',
                    riskClass: 'Optimal'
                };
            } else if (sharpe >= 0.5 && sharpe <= 1.2) {
                return {
                    title: 'Strategy: Balanced Approach',
                    className: 'assessment-balanced',
                    riskClass: 'Moderate'
                };
            } else {
                return {
                    title: 'Strategy: Inefficient Allocation (Too much Supertracker volatility for low return)',
                    className: 'assessment-inefficient',
                    riskClass: 'Suboptimal'
                };
            }
        }

        function showResults(finalCapital, totalReturn, portfolioVol, sharpeRatio, strategy) {
            // Hide allocation screen
            document.getElementById('allocationScreen').style.display = 'none';

            // Show results screen
            document.getElementById('resultsScreen').style.display = 'block';

            // Update strategy assessment
            const strategyEl = document.getElementById('strategyTitle');
            strategyEl.textContent = strategy.title;
            strategyEl.className = 'assessment-title ' + strategy.className;

            // Update final capital
            const finalCapitalEl = document.getElementById('finalCapital');
            finalCapitalEl.textContent = '$' + Math.round(finalCapital).toLocaleString();
            finalCapitalEl.className = 'metric-value ' + (totalReturn >= 0 ? 'gain' : 'loss');

            // Update total return
            const returnEl = document.getElementById('totalReturn');
            returnEl.textContent = (totalReturn >= 0 ? '+' : '') + totalReturn.toFixed(2) + '%';
            returnEl.className = 'metric-value ' + (totalReturn >= 0 ? 'gain' : 'loss');

            // Update portfolio volatility
            document.getElementById('portfolioVol').textContent = portfolioVol.toFixed(2) + '%';

            // Update Sharpe ratio
            const sharpeEl = document.getElementById('sharpeRatio');
            sharpeEl.textContent = sharpeRatio.toFixed(3);
            sharpeEl.className = 'metric-value ' + (sharpeRatio > 1.0 ? 'gain' : sharpeRatio >= 0.5 ? 'warning' : 'loss');

            // Update risk classification
            document.getElementById('riskClass').textContent = strategy.riskClass;

            // Update performance breakdown
            document.getElementById('flow1').textContent = 
                '$' + portfolio.product1.toLocaleString() + 
                ' → $' + Math.round(portfolio.product1 * MULTIPLIERS.supertracker).toLocaleString();

            document.getElementById('flow2').textContent = 
                '$' + portfolio.product2.toLocaleString() + 
                ' → $' + Math.round(portfolio.product2 * MULTIPLIERS.reverseConv).toLocaleString();

            document.getElementById('flow3').textContent = 
                '$' + portfolio.product3.toLocaleString() + 
                ' → $' + Math.round(portfolio.product3 * MULTIPLIERS.capitalGuar).toLocaleString();
        }

        function resetAllocation() {
            // Reset portfolio
            portfolio = {
                product1: 0,
                product2: 0,
                product3: 100000
            };

            // Reset sliders
            slider1.value = 0;
            slider2.value = 0;
            slider3.value = 100000;

            // Reset display
            alloc1.textContent = '$0';
            alloc2.textContent = '$0';
            alloc3.textContent = '$100,000';

            // Show allocation screen
            document.getElementById('allocationScreen').style.display = 'block';

            // Hide results screen
            document.getElementById('resultsScreen').style.display = 'none';
        }

        // Initialize
        updatePortfolio();
    </script>
</body>
</html>
