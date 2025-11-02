# Stress-Testing-with-Time-Series-Models-w-DS-Focus
Traditional credit risk models assume stable environments — but stress testing reveals how they behave under pressure. This project applies time-series forecasting to simulate credit delinquency rates across macroeconomic scenarios, echoing regulatory frameworks like Basel III and OSFI guidelines.
## Project Overview

This implementation demonstrates a comprehensive stress testing framework using statistical time-series models to quantify portfolio vulnerability under economic stress. The analysis exposes nonlinear fragility where small changes in unemployment have outsized impacts on delinquency in certain segments.

<img width="905" height="440" alt="Time Series" src="https://github.com/user-attachments/assets/6f6053b6-ea96-4479-8d78-a51911537aad" />

## Architecture

**TIER 1: PORTFOLIO FOUNDATIONS & RISK SEGMENTATION**

BUSINESS CONTEXT: Understanding portfolio composition and risk characteristics

This analysis answers:
- How is our portfolio distributed across vintages and segments?
- What are the inherent risk characteristics of different loan cohorts?
- How have underwriting standards evolved over time?

ACTIONABLE OUTPUTS:
- Portfolio segmentation for targeted risk management
- Vintage-level performance benchmarks
- Risk concentration heat maps for board reporting

**TIER 2: FORECASTING & SCENARIO ANALYSIS**

SCENARIO DESIGN FRAMEWORK:
- Baseline: Current economic conditions persist
- Mild Recession: Moderate unemployment increase (+3%), housing price decline (-10%)
- Severe Recession: Financial crisis-level stress (+7% unemployment, -25% HPI)

KEY BUSINESS QUESTIONS:
- How much could delinquency rates increase under stress?
- What are the potential credit losses in each scenario?
- How do different economic drivers impact portfolio performance?

DECISION SUPPORT:
- Informs capital planning and allocation decisions
- Supports risk appetite statement calibration
- Provides evidence for board-level risk discussions

**TIER 3: RISK CONCENTRATIONS & VULNERABILITIES**

BUSINESS CONTEXT: Identifying portfolio hotspots and concentration risks

RISK MITIGATION OPPORTUNITIES:
- Targeted underwriting enhancements for high-risk segments
- Geographic diversification strategies
- Portfolio rebalancing recommendations
- Early warning indicators for concentration risks

**TIER 4: REGULATORY & STRATEGIC IMPLICATIONS**

BUSINESS CONTEXT: Translating analysis into governance and strategy

REGULATORY CAPITAL ASSESSMENT:
- Basel III compliance: Capital ratios under stress scenarios
- ICAAP integration: Informs internal capital adequacy assessment
- Stress testing governance: Model validation and documentation

STRATEGIC DECISION SUPPORT:
- Risk appetite: Calibrating tolerance for economic stress
- Portfolio strategy: Informed by vulnerability analysis
- Capital planning: Buffer requirements for adverse scenarios
- Early warning systems: Leading indicators for risk monitoring


## 🛠️ Technical Implementation

### Data Integration
- **Source**: Freddie Mac Single-Family Loan-Level Dataset (2016)
- **Macro Variables**: Unemployment rate, HPI growth, GDP proxies
- **Preprocessing**: Robust data cleaning, synthetic feature engineering, vintage tracking

### Modeling Framework
- **Primary Model**: ARIMA with automated order selection (AIC minimization)
- **Validation**: Time-series cross-validation, persistence model benchmarking
- **Metrics**: RMSE, MAE, MAPE, forecast intervals

### Scenario Design
- **Baseline**: Current conditions persist
- **Mild Recession**: +3% unemployment, -10% HPI
- **Severe Recession**: +7% unemployment, -25% HPI (2008-style)
- **Stagflation**: +4% unemployment, -15% HPI

## Key Results

### Model Performance
- **Best Model**: ARIMA(1,0,1) with AIC = -230.77
- **Test RMSE**: 0.0233
- **Forecast Horizon**: 16 quarters (2019-2022)

### Stress Test Impacts
| Scenario | Peak Delinquency | Capital Buffer Required |
|----------|------------------|-------------------------|
| Baseline | 4.91% | - |
| Mild Recession | 5.42% | +$1.8M |
| Severe Recession | 6.17% | +$1.9M |
| Stagflation | 5.66% | +$1.8M |

### Portfolio Insights
- **Total UPB**: $1.25B across 5,000 loans
- **Average PD**: 4.01%
- **Vulnerability Level**: MEDIUM
- **High-Risk Segments**: Low-income borrowers show 3x stress sensitivity

## Data Source

[Fannie Mae and Freddie Mac Loan-Level Dataset](https://www.kaggle.com/datasets/thedevastator/2016-fannie-mae-and-freddie-mac-loan-level-datas?select=fhlmc_sf2016c_loans.csv)
