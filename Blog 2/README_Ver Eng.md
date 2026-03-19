# 1. Introduction

In the digital age, the explosion of mobile banking, e-commerce, and online payment methods has brought unprecedented convenience to users. However, the downside of this development is the rapid increase in financial fraud with increasingly sophisticated and complex methods. From credit card information theft and phishing attacks to account takeovers, cybercrime poses a serious challenge to the entire global financial system.

According to the latest data released by the Federal Trade Commission (FTC) in March 2025, consumers suffered record losses of up to $12.5 billion in 2024, a staggering 25% increase in just one year. Even more alarming, the percentage of scams resulting in actual financial losses increased from 27% to 38%, demonstrating that cybercrime is not only growing in scale but also optimizing its effectiveness through techniques such as phishing and account hijacking. Even more concerning, these attacks often occur in a split second &ndash; measured in milliseconds &ndash; rendering traditional manual verification methods completely ineffective.

Against this backdrop, the application of Machine Learning has become a key "weapon", helping banks identify and prevent unauthorized access even before transactions are completed, maximizing the security of customers' assets.

# 2. What is fraud detection in banking?

In the banking sector, fraud detection is understood as a system of processes and technologies aimed at identifying, analyzing, and preventing unusual or suspicious transactions. The core objective of this process is to protect customer assets and minimize financial losses and damage to the bank's reputation.

Nowadays, forms of fraud are becoming increasingly sophisticated, including common types such as:

- **Credit card fraud:** Unauthorized use of credit card information to make payments or withdraw money.
- **Identity theft:** Stealing personal information (ID card number, phone number) to open accounts or obtain fraudulent loans.
- **Account takeover (ATO):** Fraudsters gain control of a customer's online banking account through malware or phishing.
- **Money laundering:** Complex transactions designed to legitimize illicit funds.
- **Phishing & Social Engineering:** Scams involving text messages and calls impersonating bank employees to trick users into providing OTP codes or passwords.
- **APP Fraud (Authorized Push Payment):** Scammers trick victims into voluntarily transferring money to a fake account (often seen in lottery scams or financial investment scams).

# 3. Why Traditional Fraud Detection Methods Are No Longer Effective

Before machine learning became widely adopted, most banks relied on **rule-based systems** to detect suspicious transactions. These systems operate by applying a predefined set of rules created by analysts.

Whenever a transaction violates one of these rules, it is flagged for further review.

Some common rules used in traditional systems include:

- Transactions exceeding a certain threshold (e.g., above $5,000)
  
- Payments made from a country different from the cardholder’s usual location
  
- Multiple transactions occurring within a very short period
  
At first glance, this approach appears reasonable. However, in practice, it struggles to keep up with **rapidly evolving fraud tactics.**

The biggest limitation lies in the fact that **fraud patterns are constantly changing**. Fraudsters quickly adapt their strategies to bypass existing rules. For example, if transactions above $5,000 are flagged as suspicious, they may split a large transaction into multiple smaller ones to avoid detection. Since these rules must be manually designed and updated by experts, **the system often reacts only after new fraud patterns have already emerged**.

Another critical issue is the **high rate of false positives**, where legitimate transactions are mistakenly flagged as fraudulent. This creates inconvenience for both banks and customers. For instance, when a customer travels abroad and makes a payment in a new country, the system may interpret it as unusual activity and temporarily block the card. While the intention is to protect the account, such situations can significantly impact the user experience.

Research in financial fraud detection also indicates that rule-based systems often struggle to handle **large volumes of transaction data** and **complex fraud patterns**, where fraudulent behavior can be subtle and difficult to define using fixed thresholds.

Due to these limitations, many financial institutions are shifting toward **machine learning**, which enables systems to learn directly from transaction data, identify complex behavioral patterns, and better adapt to emerging fraud strategies.

To better illustrate the differences between rule-based systems and machine learning approaches, consider the comparison below:

| Aspect | Rule-Based Fraud Detection Systems | Machine Learning-Based Fraud Detection Systems |
|--------|-----------------------------------|-----------------------------------------------|
| **Decision-Making** | Based on fixed logic (“If X, then Y”); clear but often rigid | Evaluates multiple factors to make flexible, data-driven decisions in real time |
| **Adaptability** | Rules must be manually updated when new fraud tactics emerge | Continuously learns from data and adapts as fraud patterns evolve |
| **Explainability** | Easy to explain since decisions are tied to specific rules | Less intuitive, but many systems provide tools to interpret model decisions |
| **Accuracy & Performance** | Effective for known fraud patterns but prone to high false positives | Higher accuracy, reducing both false positives and missed fraud cases |
| **Scalability** | Becomes difficult to manage as transactions and rules increase | Scales efficiently to handle large volumes of data without added rule complexity |
| **Customer Experience** | Strict rules may block legitimate transactions, causing frustration | Balances security with a smoother experience for trusted customers |
| **Fraud Readiness** | Reactive: responds after threats appear | Proactive: capable of adapting to new fraud strategies |
<p align="center">
   <img src= style="margin: 0 auto; display: block;"><br/>
    <em>Table 3.1. Comparison between traditional rule-based fraud detection systems and machine learning-based systems
  ; <br/>Source: <a href="https://www.signifyd.com/blog/rules-based-vs-machine-learning-fraud-protection/">Channing Lovett</a> </em>
 </p></em>
 </p>

