# Jev vs Laya vs Haiku: the questions

Every model got the same question and the same options for each item. The items themselves aren't here: the emails are from a real inbox and the reviews are real people's.

Jev and Laya take the question and options as structured fields. Haiku got them as this prompt, with a schema forcing one of the options:

```
{the item's text}

Question: {question}
Options:
- {option}
- {option}

Answer with the single best option and your confidence (0 to 1) that it is correct.
```

## Inbox sorting

**Question:** Which category best describes this email in one person's inbox?

**Options:**
- spam: unwanted junk or a scam from an unknown or shady sender: phishing, fake account warnings, prize or gambling bait, get-rich schemes, knockoff resellers
- marketing: a real business promoting its products, sales, deals or content, including newsletters that mainly sell something
- package tracking: shipping updates for a physical order: shipped, out for delivery, delivered, delayed
- order receipt: an order confirmation or receipt for something bought online or in a store (not a subscription and not a food or grocery order)
- food delivery: a food or grocery delivery or pickup order: confirmation, receipt, or status update
- subscription receipt: a receipt, invoice or renewal notice for a recurring subscription, membership or software plan
- access code: a one-time code, verification code, magic sign-in link or password reset for logging in
- other: anything else: news, account or security alerts, bank statements, social notifications, personal or work email

## Support tickets, 5 teams

Planwell is a made-up project-management app.

**Question:** Which team should handle this customer message for Planwell, a project-management app?

**Options:**
- Billing: charges, invoices, refunds, plan changes and payment methods
- Technical support: bugs, errors, performance, integrations, imports and exports
- Account and access: logging in, passwords, security, teammates, permissions and account settings
- Sales and pre-sales: pricing, demos, trials, contracts and questions from people who have not bought yet
- Product feedback and other: feature requests, praise, complaints, how-to questions and anything else

## Support tickets, 70 issues

**Question:** What is the main issue in this customer message for Planwell, a project-management app?

**Options (each model saw the description only):**
- duplicate charge for the same period
- wants money back for a charge
- wants to stop paying and cancel
- wants a cheaper plan
- wants a bigger plan or more features
- needs an invoice or receipt
- company name, address or tax ID on the invoice is wrong
- card declined or payment didn't go through
- wants to change the payment method
- price went up or the charge is higher than expected
- billed for more users than they have
- wants to switch billing frequency
- asking about a promo, nonprofit or student discount
- sales tax, VAT or tax exemption
- the web app is blank, stuck or won't open
- the app is laggy or pages load slowly
- the phone app crashes or freezes
- not getting emails or push alerts, or getting too many
- changes don't show up across devices or teammates
- can't attach or upload files
- Slack integration broken or setup help
- Google Calendar or Drive integration issue
- GitHub integration issue
- developer getting errors from the API
- moving data in from Trello, Asana or a spreadsheet
- wants to export their projects or data
- tasks, comments or projects disappeared
- a specific feature behaves wrong (recurring tasks, due dates, search)
- can't sign in, wrong password or error on login
- reset email never shows up
- lost phone or authenticator, locked out by two-factor
- wants to change the account email address
- wants their account or data deleted
- single sign-on (Okta, Google Workspace) setup or errors
- can't invite someone, or the invite never arrives
- wants to remove a former employee
- who can see or edit what, admin rights
- wants to hand the workspace to someone else
- has duplicate accounts to combine
- rename or change the workspace URL
- saw a login they don't recognize
- believes someone took over the account
- how much it costs, what's in each plan
- wants a demo or a sales call
- large team wanting custom pricing or a contract
- wants more time on the free trial
- how it compares to Asana, Monday or Jira
- asks whether a feature exists before buying
- needs a W-9, vendor form or purchase order
- IT wants security or compliance documents
- reseller, agency or partnership pitch
- school or nonprofit asking about eligibility
- wants help switching before they commit
- asking for a price break for many seats
- legal wording, terms of service or data agreement
- wants training or onboarding for their team
- wants something new added
- cosmetic glitch or small annoyance
- dislikes a design change or the layout
- just saying thanks or that they love it
- frustrated in general, no single issue
- screen reader, contrast or keyboard access issue
- wants another language or a translation fix
- appearance and theme requests
- can't find how to do something in the help docs
- how do I do a specific thing in the app
- spam, sales pitch or wrong company
- journalist or media request
- subpoena, copyright or law-enforcement request
- says the whole service seems down

## Google review to star rating

**Question:** How many stars (1 to 5) did this reviewer give the business?

**Options (no numbers in the text, because plain "1 star" labels broke Laya):**
- very negative, a terrible experience
- mostly negative, several real problems
- mixed, some good and some bad
- mostly positive with minor complaints
- very positive, an excellent experience
