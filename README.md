# Game of Thrones: Character Social Fingerprints Through Dialogue Analysis

**Course:** DATA200 Midterm Project

## Research Question

**"How do different Houses address individual characters in Game of Thrones, and what does this reveal about each character's 'social fingerprint' within the political landscape?"**

This project investigates the "political fingerprint" of Westeros by analyzing how characters are spoken to by different Houses. Using computational linguistics, I map the social hierarchy and reputation dynamics of the Seven Kingdoms.

## Project Overview

This Jupyter notebook contains a complete computational linguistics analysis of Game of Thrones dialogue data. The analysis follows a structured pipeline from data cleaning through statistical modeling, combining sentiment analysis, network analysis, and keyword extraction to understand character reputation and social positioning.

### Analysis Pipeline

1. **Setup and Data Loading** - Import libraries (pandas, numpy, matplotlib, networkx, VADER) and load the Kaggle Game of Thrones script dataset
2. **Data Cleaning and Preprocessing** - Use regex to clean character names, remove generic characters, filter to top 20 characters
3. **House Allegiances** - Manually assign 20 main characters to 6 major houses (Stark, Lannister, Targaryen, Greyjoy, Baratheon, Tyrell)
4. **Sentiment Analysis** - Apply VADER to measure emotional tone of each dialogue line (positive, negative, neutral, compound scores)
5. **House-Specific Keywords** - Extract house vocabulary patterns using regex (locations, values, symbols, titles)
6. **Social Dynamics Patterns** - Identify linguistic markers of loyalty, power, respect, and addressing style
7. **Reputation Metrics** - Calculate incoming sentiment, respect, and power directed at each character
8. **Character-Level Aggregation** - Aggregate line-level features to character level using groupby operations
9. **Network Graph** - Visualize top 10 character interactions with NetworkX (nodes sized by PageRank centrality)
10. **Reputation Matrix** - Create weighted heatmap showing how different houses address specific characters
11. **Statistical Modeling** - Test linear regression: does PageRank predict reputation?
12. **Conclusion** - Summarize findings, limitations, and future modeling extensions

## Key Findings

### House-Specific Communication Styles
- **House Targaryen**: Assertive, positive rhetoric focused on justice and legitimacy (avg compound sentiment: +0.038)
- **House Stark**: Neutral, duty-bound speech with highest neutral scores (0.816)
- **House Greyjoy**: Confrontational and negative communication style (only house with negative sentiment: -0.020)
- **House Lannister & Baratheon**: Moderate sentiment with variable patterns

### Power Dynamics and Networks
- **Jon Snow** serves as the primary conversational hub with the highest PageRank, connecting disparate factions
- **Network Centrality**: Targaryen and Lannister characters dominate through command-based dialogue patterns
- **Interaction Style**: Power is primarily negotiated through formal, one-on-one interactions rather than public declarations
- **Most Common Pattern**: Formal respect markers (404 occurrences), while group addressing is rarest (94 occurrences)

### Reputation Polarization
- **Jon Snow**: Bifurcated perception—lower status under Stark name, highly prestigious under Targaryen banner
- **Tyrion Lannister**: Faces internal house friction with negative sentiment from Lannisters (-0.01) despite strategic value
- **The Targaryen Advantage**: House Targaryen affiliation consistently yields the highest reputation scores
- **Bronn**: Highest sentiment score (0.029) and massive respect rate (0.33)

### Statistical Modeling
- **R² = 0.23**: PageRank explains only 23% of reputation variance; 77% is influenced by other factors
- **Implication**: Talking frequency doesn't directly correlate with reputation—other social factors play significant roles

## Data & Methodology

### Data Source
- **Dataset**: Kaggle - Game of Thrones Script (All Seasons)
- **Size**: Top 20 characters, ~8,000+ dialogue lines from major houses

### Techniques Used

| Technique | Purpose |
|-----------|---------|
| **VADER Sentiment Analysis** | Measure emotional tone (positive/negative/neutral/compound) |
| **Regex Pattern Matching** | Extract house-specific keywords and social markers |
| **Network Analysis (NetworkX)** | Calculate PageRank centrality and interaction patterns |
| **Hierarchical Weighting** | Model interaction intensity (80% direct, 30% turn-window, 10% ambient) |
| **Linear Regression** | Test predictive relationship between network centrality and reputation |

### Key Regex Patterns

- **House Locations**: Winterfell, Casterly Rock, Dragonstone, Iron Islands, etc.
- **House Values**: "Honor", "Gold", "Fire and Blood", "We Do Not Sow", etc.
- **Social Dynamics**: Loyalty markers ("I serve", "oath"), Power markers ("command", "must"), Respect ("Your Grace", "Ser")

## Installation & Usage

### Prerequisites
```bash
Python 3.7+
Jupyter Notebook
```

### Required Libraries
```bash
pip install pandas numpy matplotlib seaborn networkx vaderSentiment kagglehub
```

### Running the Notebook
```bash
jupyter notebook GoT-Dialogue-Analysis.ipynb
```

The notebook will:
1. Automatically download the Game of Thrones script dataset from Kaggle
2. Process and clean the dialogue data
3. Generate visualizations (network graphs, heatmaps, regression plots)
4. Output character-level statistics and reputation metrics

## Visualizations Generated

1. **Network Graph**: Top 10 character interaction network with node sizing by PageRank
2. **Reputation Matrix**: Heatmap showing weighted sentiment scores across houses and characters
3. **Regression Plot**: PageRank vs. Reputation sentiment with trend line (R² = 0.23)
4. **Sentiment Distribution**: House-specific emotional communication patterns

## Limitations & Future Work

### Current Limitations

1. **Regex Context Blindness**: Cannot distinguish between "the north" as direction vs. political entity
2. **Missing Vocal Cues**: Text-only analysis misses sarcasm, irony, and emphasis patterns
3. **Simplistic Weighting Model**: Hierarchical interaction model (80/30/10) may oversimplify complex conversational dynamics
4. **Data Exclusion**: 44.4% of data excluded (minor houses and generic characters) limits broader social context
5. **Domain Knowledge Requirement**: Manual identification of houses, locations, and character allegiances required; not generalizable to new datasets
6. **Temporal Dynamics**: Static house assignments cannot capture characters who change allegiances (e.g., Theon, Jaime's redemption arc)
7. **Sample Imbalance**: Characters with minimal dialogue difficult to analyze accurately

### Future Enhancements

- **Outlier Removal**: Filter extreme data points (e.g., Sandor) before regression modeling
- **Multiple Regression**: Control for confounding variables (house affiliation, screen time, character role)
- **Time-Series Analysis**: Track communication style and reputation evolution across seasons
- **Interaction Effects**: Test whether power language has different reputational effects by house context
- **Machine Learning Classification**: Predict character house allegiance from dialogue patterns alone
- **Sarcasm Detection**: Integrate more sophisticated NLP models to detect irony and emphasis
- **Dynamic Weighting**: Develop adaptive weighting based on scene context and character relationships

## Conclusions

The data reveals a strong correlation between House address and social status. While I can observe broad reputation shifts (e.g., Jon Snow's polarized perception), the analysis demonstrates that **"social fingerprints" remain incomplete without accounting for sarcasm, irony, and shifting allegiances** that define the true complexity of Westeros politics.

The 23% R² value from our regression model suggests that **network centrality alone is insufficient to predict reputation**—other social, political, and contextual factors play equally important roles in determining a character's standing in the Seven Kingdoms.


## Dataset Citation

Source: [Kaggle](https://www.kaggle.com/datasets/albenft/game-of-thrones-script-all-seasons)


## References

- VADER Sentiment Analysis: C. Hutto and E. Gilbert, "VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text" (2014)
- NetworkX Documentation: https://networkx.org/
- Game of Thrones Series: George R. R. Martin (HBO Adaptation)
