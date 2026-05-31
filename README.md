# Financial Mathematics: Tree Pricing Library Extension

## Overview
This project was developed as part of the Financial Mathematics course (A.A. 2025/2026). The goal was to extend the Java-based `net.finmath.tree` option pricing library to support more complex market realities, specifically focusing on long-dated products and exotic derivatives. 

## Key Features Developed

### 1. Dividend Modeling
We introduced a flexible representation of dividends that corrects the systematic overestimation of underlying asset values in long-dated options.
* **Implemented Models:** `DiscreteProportionalDividend` and `ContinuousDividendYield`.
* **Tree Integration:** Integrated into three recombining tree models: Cox-Ross-Rubinstein (CRR), Jarrow-Rudd (JR), and the Boyle Trinomial model.
* **Architecture:** Utilized **Dependency Injection**. The dividend logic is injected into the tree models at runtime, ensuring total backward compatibility with the original library.

### 2. Barrier Options Pricing Engine
We built a new product class (`BarrierOptionsProducts`) capable of pricing all eight barrier variants (Up/Down, In/Out, Call/Put).
* **Pricing Logic:** Instead of implementing a backward induction for each type, we leveraged the **IN-OUT parity**. 
* **Rebate Handling:** The parity was successfully extended to account for cash rebates when a barrier is touched.
* **Validation:** The tree-based prices for barrier options were successfully tested for convergence against the analytical Black-Scholes closed-form formulas.

## Technical Highlights
* **Language:** Java
* **Design Patterns:** Dependency Injection, Interface-driven development (e.g., `DividendModel` and `MultiplicativeDividendModel` interfaces).
* **Testing:** Automated tests confirmed that early exercise becomes rational for American Calls when sufficiently large dividends are introduced ($V_{Am} > V_{Eu}$). 

## Authors
* Benassi Martina
* Consiglio Giuseppe
* Cortivo Davide
* Menarbin Samuele
