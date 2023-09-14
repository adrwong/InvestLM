![r.jpg](https://x.imgs.ovh/x/2023/09/14/6502da25e646d.jpg)
---
This is the repo for the new financial domain large language model, **InvestLM**, tuned on LLaMA-65B[1], using a carefully curated instruction dataset related to financial investment. We provide guidance on how to use InvestLM for inference.

# Overview

Inspired by less-is-more-for-alignment (LIMA)[2], we manually curate a small yet diverse instruction dataset, covering a wide range of financial related topics, from Chartered Financial Analyst (CFA) exam questions to SEC filings to Stackexchange quantitative finance discussions. InvestLM shows strong capabilities in understanding financial text and provides helpful responses to investment related questions.

# Training Format
**Prompt with input:**
```
Below is an instruction that describes a task, paired with further context. 
Write a response that appropriately completes the request.

Instruction:
{instruction}

Input:
{input}

Response:
```

**Prompt without input:**
```
Below is an instruction that describes a task, paired with further context. 
Write a response that appropriately completes the request.

Instruction:
{instruction}

Response:
```

# Inference 
First, please install the required packages.
```
pip install -r requirements.txt
```
Then, run inference.py.

```
python inference.py \
    --base_model "" \
    --lora_weights ""
```

# Generation Examples
## Investment Advice
**Instruction:**
Leading the percentage decliners list this morning is HEICO Corp. (HEI - $9.42 to $158.43) after the provider of aerospace & defense components reported Q3 earnings of $0.74 per share ($0.01 beat) on revenue that rose 26.9% year-over-year to $722.9M (above the $701.55M expected). The stock may be trading lower today due to Q3 adjusted EBITDA ($179.8M vs. the $181.7M expected) and Q3 operating margin (20.7% vs. 22.6% expected). Calls are outnumbering puts ~2:1 with the September 15th 180.00 call seeing the most action from traders (volume is 136).

Can you suggest a trading strategy based on this news?

**Response:** Based on the information you provided, I would consider executing a bear put spread on HEI stock. Since I'm bearish on HEI based on the earnings miss, I would buy a put with a lower strike price and simultaneously sell a put at a higher strike price to offset some of the cost of the position. This strategy will profit if HEI stock continues to fall through the lower strike price. The strategy will begin to lose value if HEI stock rallies above the higher strike price.
## Earnings transcript summarization
**Instruction:**
Please give the bullet point summarization of the following long earnings call transcripts.   

**Input:**
For the third quarter of 2021, revenues increased to $225.3 million compared to $116.6 million in the third quarter of the prior year.Operating profit for the third quarter was $8 million compared to an operating loss of $31.8 million in the same quarter of the prior year.EBITDA for the third quarter was $26.5 million compared to EBITDA of negative $12.3 million in the same quarter of the prior year.Our diluted earnings per share for the third quarter were $0.02 compared to an $0.08 loss per share in the same quarter of the prior year.Cost revenues -- cost of revenues during the third quarter of 2021 was $170.6 million or 75.7% of revenues compared to $100.9 million or 86.5% of revenues during the third quarter of 2020.Selling, general and administrative expenses were $31.4 million in the third quarter of 2021 compared to $32.4 million in the third quarter of the prior year.Selling, general and administrative expenses decreased from 27.8% of revenues in the third quarter of last year to 14% of revenues in the third quarter of 2021 due to leverage of higher revenues over costs that are relatively fixed during the short term.Depreciation was $18.1 million in the third quarter of 2021 compared to $18.7 million in the same quarter of the prior year.Our Technical Services segment revenues for the third quarter were $211.8 million compared to $109.3 million in the same quarter last year due to significantly higher activity and some pricing improvement.Segment operating profit in the third quarter of 2021 was $8.3 million compared to a $24.9 million operating loss in the third quarter of the prior year.Our Support Services segment revenues for the third quarter of this year were $13.5 million compared to $7.3 million in the same quarter last year.Segment operating loss in the third quarter was $55,000 compared to an operating loss of $3.8 million in the third quarter of the prior year.On a sequential basis, RPC's third quarter revenues increased 19.4% to $225.3 million from $188.8 million in the prior quarter.Cost of revenues during the third quarter of 2021 increased 17% to $170.6 million compared to $145.8 million in the prior quarter.As a percentage of revenues, cost of revenues decreased slightly from 77.2% in the second quarter of this year to 75.7% in the third quarter of 2021, reflecting some pricing improvement and operating expense leverage.Selling, general and administrative expenses during the third quarter of 2021 increased 6.9% to $31.4 million from $29.4 million in the prior quarter, resulting in positive operating expense leverage.As a result of these improvements, operating profit during the third quarter of 2021 was $8 million compared to an operating loss of $1.2 million in the prior quarter.RPC's EBITDA was $26.5 million in the third quarter compared to EBITDA of $17.3 million in the prior quarter.Our Technical Services segment revenues increased by $35.7 million or 20.3% in the third quarter due to increased activity levels and some pricing improvement in the segment service lines.RPC's Technical Services segment generated an $8.3 million operating profit in the current quarter compared to an operating profit of $1.4 million in the prior quarter.Our Support Services segment revenues increased by 6.6% to $13.5 million in the third quarter.Operating loss was $55,000 in the current quarter compared to an operating loss of $2.4 million in the prior quarter.This equipment was added late in the third quarter and is reflected as a finance lease on our balance sheet with a balloon payment due at the end of 12 months.Third quarter 2021 capital expenditures were $19 million, excluding the equipment acquired under a finance lease in the third quarter.We currently estimate full year 2021 capital expenditures, excluding lease financed equipment, to be approximately $65 million, comprised primarily of capitalized maintenance for existing equipment and selected growth opportunities.At the end of the third quarter, RPC's cash balance was approximately $81 million, and we remain debt-free.

**Response:** 
Third Quarter 2021 Summary

Q3 2021 Revenue increased 91.3% YoY to $225.3 million. Operating profit was $8 million compared to an operating loss of $31.8 million in the same quarter last year. EBITDA for the third quarter was $26.5 million compared to negative $12.3 million in the same quarter of the prior year. Diluted EPS for the third quarter were $0.02 compared to an $0.08 loss per share in the same quarter of the prior year. Cost of revenues for the third quarter of 2021 were 75.7% of revenues compared to 86.5% of revenues in the same quarter of the prior year. SG&A expenses decreased from 27.8% of revenues in the third quarter of last year to 14% of revenues this quarter due to leverage of higher revenues over costs that are relatively fixed in the short term. Technical Services segment revenues for the third quarter were $211.8 million compared to $109.3 million in the same quarter last year due to higher activity and some pricing improvement. Segment operating profit in the third quarter of 2021 was $8.3 million compared to a $24.9 million operating loss in the third quarter of the prior year. Support Services segment revenues for the third quarter of this year were $13.5 million compared to $7.3 million in the same quarter last year. The company reported sequential revenue increase of 19.4% in Q3 2021 to $225.3 million, compared to $188.8 million in the previous quarter. Cost of revenues in the third quarter of 2021 increased 17% to $170.6 million compared to $145.8 million in the prior quarter. As a percentage of revenues, cost of revenues decreased slightly from 77.2% in the second quarter to 75.7% in the third quarter of 2021, reflecting some pricing improvement and operating expense leverage. RPC's Technical Services segment revenues increased by $35.7 million or 20.3% in the third quarter due to increased activity levels.


# Ethics Statement
It is essential to recognize that the responses from InvestLM  should not be construed as definitive investment advice. All investment strategies and decisions should be made after careful consideration of one's financial situation, risk tolerance, and investment goals. We strongly advocate for potential investors to consult with professional financial advisors and consider multiple information sources before making any investment decisions. Relying solely on InvestLM 's outputs without thorough due diligence can lead to unintended financial consequences. Thorough analyses should be conducted to understand the strengths and weaknesses of InvestLM .


# References
[1]: LLaMA: Open and Efficient Foundation Language Models. Hugo Touvron, Thibaut Lavril, Gautier Izacard, Xavier Martinet, Marie-Anne Lachaux, Timothée Lacroix, Baptiste Rozière, Naman Goyal, Eric Hambro, Faisal Azhar, Aurelien Rodriguez, Armand Joulin, Edouard Grave, Guillaume Lample. https://arxiv.org/abs/2302.13971v1

[2]: LIMA: Less Is More for Alignment. Chunting Zhou, Pengfei Liu, Puxin Xu, Srini Iyer, Jiao Sun, Yuning Mao, Xuezhe Ma, Avia Efrat, Ping Yu, Lili Yu, Susan Zhang, Gargi Ghosh, Mike Lewis, Luke Zettlemoyer, Omer Levy. https://arxiv.org/abs/2305.11206
