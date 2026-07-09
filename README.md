# PensionFundSimulator

A stochastic simulation model to estimate the future liabilities of a defined benefit pension scheme.
The model uses Monte Carlo simulation to generate thousands of possible future economic scenarios and calculates the present value of pension obligations under uncertainty.

The simulation incorporates:
- Salary growth uncertainty
- Longevity risk
- Stochastic discount rates
- Liability stress testing

The objective is to demonstrate how actuarial assumptions influence pension scheme funding requirements.

Defined benefit pension schemes promise members a fixed retirement income based on a formula involving salary and service.
Unlike defined contribution schemes, the employer bears the investment and longevity risks.

Accurately estimating future liabilities is therefore critical for:
- Pension scheme funding decisions
- Investment strategy
- Risk management
- Trustee decision-making
Small changes in assumptions, such as discount rates or life expectancy, can significantly impact the value of liabilities.

# Model Overview

The simulator follows these stages:
Synthetic Members -> Salary Projection -> Retirement Pension Calculation -> Longevity Simulation -> Discount Rate Simulation -> Present Value Calculation -> Monte Carlo Simulation -> Risk Analysis

# Data Generation

No real member data is used, instead a synthetic population of 1,000 pension members was created.
Each member has:

Age: 25-65 years
Gender: M/F
Salary: Normally distributed around £35,000 (Roughly average uk salary)
Years of service = Randomly generated based on age

# Assumptions

Salary growth is modelled as:
Salary(t+1) = Salary(t) × (1 + growth + random shock)

Annual pension is determined by:
Pension = Years of Service × Accrual Rate × Final Salary
Where accrual rate = 1/60

Members retire at age 65.
Post-retirement lifespan is simulated using a normal distribution where: Mean = 20 years, Standard deviation = 5 years
Values are restricted between 5 and 40 years.

# Monte Carlo Simulation

The model runs:
10,000 simulations

Each simulation creates a different possible future based on:
- Salary uncertainty
- Mortality uncertainty
- Interest rate uncertainty
The output is a distribution of possible pension liabilities.

# Key Outputs

The model calculates:
- Mean liability
- Median liability
- 95th percentile liability
- Value at Risk

# Stress Testing

The model evaluates different scenarios:

Scenario: Discount rates decrease by 1%
Impact: Lower discount rates increase liabilities.

Scenario: Members live two years longer.
Impact: Additional pension payments increase liabilities.
