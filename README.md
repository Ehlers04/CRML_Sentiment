# Sentiment Analysis: Project Tanbreez (X / Twitter)

## Purpose
This project assesses public emotion-based sentiment around **“Project Tanbreez”** using posts collected from **X (formerly Twitter)**. The goal is to capture whether the discourse shows **negative affect**, **neutral affect**, or **positive affect**, and to support a strategy report with an evidence-based snapshot of online sentiment.

## Sentiment Method
Sentiment is computed as **emotion-based polarity** on a scale from:

- **-1** = negative affect  
- **0** = neutral affect  
- **+1** = positive affect  

The analysis uses **VADER (Valence Aware Dictionary and sEntiment Reasoner)** from the NLTK library. VADER is designed for short, informal social media text and produces a **compound score** between **-1 and +1**, which is used as the primary sentiment metric.

**Interpretation guideline (compound score):**
- compound **≥ 0.05** → positive  
- compound **≤ -0.05** → negative  
- otherwise → neutral  

## Data Source and Collection (Manual)
Posts were collected manually using **X Advanced Search** with the keyword:

- `"Project Tanbreez"`

### Timeframe
- **01.01.2025 – 31.01.2026**

### Filters and Exclusions
To improve relevance and reduce noise:
- **Excluded replies** (to focus on standalone posts rather than conversational fragments)
- **Excluded posts with fewer than 10 likes** (to reduce low-visibility content and noise)
- **Excluded posts from “Tony Sage”**  
  Rationale: to avoid over-representation of investment-related advertisement or promotional posting behavior.

### Rationale for relevance filtering
The ≥10 likes threshold was applied as a **pragmatic relevance filter** to prioritize posts with demonstrated visibility/engagement and to reduce the likelihood of collecting low-signal content.

## Data Format
Collected posts are stored in a structured table (e.g., CSV) with:
- `text` — post content used for sentiment scoring


## Output
The scoring process produces VADER sentiment fields for each post:
- `neg`, `neu`, `pos` — proportions of negative/neutral/positive sentiment
- `compound` — overall sentiment score from **-1 to +1** (primary metric)

## Limitations
- The dataset is **not a full census** of all posts within the timeframe; it is a manually curated sample.
- Using a ≥10-like threshold can introduce **sampling bias** toward higher-engagement or more polarizing content.
- Lexicon-based sentiment tools (including VADER) can misinterpret sarcasm, context, or domain-specific finance language.

## Reproducibility Notes
To reproduce sentiment scoring, ensure:
- Python environment has `nltk` and `pandas`
- VADER lexicon is available via `nltk.download("vader_lexicon")`

---

**Project keyword:** Project Tanbreez  
**Platform:** X Advanced Search  
**Timeframe:** 01.01.2025 – 31.01.2026  
**Exclusions:** Tony Sage; posts <10 likes; replies
