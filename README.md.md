# CA2: Sciar Tips

**Live site:** <https://kartikb-hub.github.io/Sciar-Tips-CA-2/>  
**Repository:** <https://github.com/KartikB-hub/Sciar-Tips-CA-2>

**My question:** Can the lowest-paid person at Halloran's see why more hours did not bring more tips, and ask about it without being named?

Sciar, Halloran's, their people and every figure here are invented for the NCI teaching case (H9LOCHFFT CA2). Pages: [`index.html`](index.html) (for restaurant owners) and [`app.html`](app.html) (staff view). Data: `data/` (copied unchanged from the pack). AI sessions: [`ai-log/`](ai-log/).

## Part 1: The people

**Internal: Aoife (CEO).** Need: a staff product that works on phones. "Make it work on a phone. Nearly all restaurant staff only have phones." (`04-aoife.md`)

**External: Rafael (kitchen porter).** Need: to see how his pay is counted, and to ask without being identified. "i dont understand how they count it"; "please dont say it was me who ask." (`01-rafael.md`)

**Accessibility and culture:** "His first language is Portuguese" and "my phone screen is broken so i cannot read the page good" (`01-rafael.md`). So the staff view opens on one large number, uses 18px+ text and tap-to-pick question topics, and has a Portuguese toggle.

## Part 4a: Theory behind the build

**Leadership: paternalistic leadership** (Farh and Cheng, 2000; Pellegrini and Scandura, 2008), which pairs strong authority with personal care. Declan decides what staff need ("They don't need the formula, they need the money", `02-declan.md`) and gives personal favours ("he is good to me with my visa letter", `01-rafael.md`). It explains why Rafael is grateful and afraid at once: care creates a debt that makes questions feel disloyal ("i dont want problem with Declan"). What it misses: the outcome comes from a rule, not just a person. In `payouts.csv` (staff_id = S12), 178.5 of Rafael's 527.5 hours (33.8%) fall after 23:00 and earn nothing, against 2.6% for the floor side.

**Culture: organisational silence** (Morrison and Milliken, 2000). Niamh writes "Nobody has ever complained about the split. Not once in twelve weeks" (`03-niamh.md`), yet Rafael says "i ask Niamh one time in september and she say is the system, is fair for everybody" (`01-rafael.md`). A question was asked and closed, so it never counted. The only voice route is "they come to me", which leads to the split's defender.

**How it shaped the build:** because voice runs up the hierarchy, the question in `app.html` goes to Sciar, not the restaurant. It is private by default, the sender chooses whether it is shared, and the page warns a one-person role that the topic alone could identify them.

**Competitive advantage:** hiding the rule pleases the paying owner, but leaves Sciar a payment rail any POS can copy. A staff view people can check is a rarer, harder-to-imitate resource (Barney, 1991): inferred, since the pack has no retention evidence.

**Limit:** both theories look inside one firm, so neither explains a six-person start-up's dependence on one reference customer; and paternalism research comes mainly from Chinese family firms, so applying it here is my assumption.

## Part 4b: Decision record

**Decision 1: a request I changed. "Keep the split rule visible to the owner only"** (Declan, `02-declan.md`; Aoife item 2, `04-aoife.md`)

|                               |                                                                                                                                                                                                                                |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Options**                   | \(a\) Hide the rule, as asked. (b) Show everyone's points and hours. (c) Show each person only their own rate, points and the week's totals. Show colleagues only in groups of 3 or more.                                      |
| **Criteria**                  | Can a worker check their own pay? Is any colleague's pay or hours shown? Do we keep our only customer?                                                                                                                         |
| **What decided it**           | With (a), Rafael cannot check why his pay is "same like before". Declan's worry is staff "counting each other's hours". Option (c) shows nobody else's hours, so it answers his worry and still explains the pay. I chose (c). |
| **What would change my mind** | Proof from the pilot that showing the sum caused fights between named staff, or Halloran's leaving. Then I would raise it openly with Aoife, not hide it.                                                                      |

How the build still helps Declan: he wants a calm team and a product owners trust. The staff view shows no single colleague, does not judge his rule, and sends questions privately to Sciar, not to the whole team. I also said no to "Fully compliant with Irish tips law" and the 34% figure, because the pack does not prove them. I kept the true part of "100% of tips go to the team", with its source.

**Decision 2: an AI suggestion I rejected. "Unrecorded extra hours"**

|                               |                                                                                                                                                                                             |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Options**                   | \(a\) Trust the AI summary of `01-rafael.md`, which said the problem was "unrecorded extra hours", and build an hours-tracking feature. (b) Check the data first.                           |
| **Criteria**                  | What `payouts.csv` really shows.                                                                                                                                                            |
| **What decided it**           | Rafael's hours are recorded: 48.5 to 55 hours a week in weeks 9 to 12 (staff_id = S12). The problem is the 20 to 21.5 hours after 23:00 that earn nothing. So I showed that number instead. |
| **What would change my mind** | Proof that the rota misses hours. Rafael says "i finish 1am, sometimes later", and the data cannot show if that is fully counted.                                                           |

**A bias I caught:** trusting the AI too quickly. When the first AI tool gave me a summary of Rafael's message, I nearly took "unrecorded extra hours" as fact. When I opened `payouts.csv`, his hours were there. After that I checked every AI summary against the real files before using it.

## Part 4c: The Struggle (written without AI)

I used my claude Ai tool to get the summary and the motive of the assignment, so that i can plan and think exactly what should be covered in my answers.

i got confused in understanding about the commit hash, initially i was not sure on which data to collect and upload in the field of commit hash.

Ai tool read the short summary of rafaels's short message which said "unrecorded extra hours", so i checked the raw files instead and payout.csv files there it showes that his hours were recorded and the real cause was the after 23:00 rule which says the tip won’t be counted after this time.

What differently i did is, did not blindly believe the data given by Ai, but cross checked the data files.

Instead of giving Ai to summaries the assignment to me, i would read it completely and then give it to the Ai tool and check if i have understand properly or misunderstood some topics and even argue with Ai if i believe i am right. i would like to understand every term before starting the assessment for example, i did not know about commit hash and if i knew it before deploying the github repo then i would have tried creating more commit hashs.

26557bd in this commit hash i have uploaded a app.html file which i developed with the help of Ai.

### Assumptions and evidence checks (supporting notes)

| Claim (file)                                                | Observed in data                                                               | Used how                                        |
|-------------------------------------------------------------|--------------------------------------------------------------------------------|-------------------------------------------------|
| "every cent of the card tips goes out" (`02-declan.md`)     | Card tips €31,754.13 (takings.csv); paid €31,754.09 (payouts.csv); 4c rounding | True for card tips; on landing page with source |
| Service charge is the house's (`02-declan.md`)              | €9,004.69 on 65 of 72 days, service_charge_paid_to = house (takings.csv)       | Shown to staff as a fact; no legal comment      |
| "Nobody has ever complained" (`03-niamh.md`)                | Contradicted by Rafael's September question (`01-rafael.md`)                   | Part 4a                                         |
| "chefs are on a better hourly rate" (`03-niamh.md`)         | No wage data in the pack                                                       | Not used                                        |
| 34% retention, "only fully compliant" (`05-market-scan.md`) | No source attached                                                             | Refused                                         |

- The demo selector in `app.html` stands in for sign-in; the real product would show each person only their own rows.
- Concerns are simulated in `localStorage` (this browser only), as the page says.
- Groups shown to staff: floor side (8 people) and kitchen side (5, then 4 from week 9). Kitchen porter (2, then 1) and bar (2) are never shown alone.
- Portuguese text was drafted with AI and not checked by a native speaker (stated on the page).

### References

Barney, J. (1991) 'Firm resources and sustained competitive advantage', Journal of Management, 17(1), pp. 99–120.  
Farh, J.L. and Cheng, B.S. (2000) 'A cultural analysis of paternalistic leadership in Chinese organizations', in Li, J.T., Tsui, A.S. and Weldon, E. (eds) Management and Organizations in the Chinese Context. London: Macmillan, pp. 84–127.  
Morrison, E.W. and Milliken, F.J. (2000) 'Organizational silence: a barrier to change and development in a pluralistic world', Academy of Management Review, 25(4), pp. 706–725.  
Pellegrini, E.K. and Scandura, T.A. (2008) 'Paternalistic leadership: a review and agenda for future research', Journal of Management, 34(3), pp. 566–593.
