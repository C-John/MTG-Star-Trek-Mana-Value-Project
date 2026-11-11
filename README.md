# Predicting Card Mana Value in the MTG Star Trek Set

An automated machine learning model and interactive analytical dashboard designed to reverse-engineer the underlying mana pricing formula of Magic: The Gathering cards using real-world data from the Star Trek (TRK) set.

---

## 📊 Interactive Dashboard
👉 **[View the Published Tableau Dashboard](https://public.tableau.com/views/PredictingCardManaValueintheMTGStarTrekSet/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**  
*Explore the game balance scatter plot, error distributions, and key feature importance breakdown.*

---

## 🎯 Executive Summary
I used a **Random Forest machine learning model** I learned from the [Google Advanced Data Analytics Professional Certificate](https://www.coursera.org/organizations/gwg-ent-first-work/professional-certificates/google-advanced-data-analytics) to deconstruct and predict the mana value formula of Magic: The Gathering cards from the Star Trek expansion set. I extracted live JSON data via the [**Scryfall API**](https://api.scryfall.com/cards), processing **647 mechanically unique castable cards**, utilizing Natural Language Processing (NLP) techniques to engineer 62 features from unstructured ability text, card types, colour identities, and base stats (power/toughness).

### Key Performance Metrics:
* **Exact Match Rate (Accuracy):** `51.5%` — Over half of all cards adhere strictly to an underlying mathematical cost formula.
* **Mean Absolute Error (MAE):** `0.70` — When the model misses the exact printed cost, its prediction is off by less than 1 mana on average.

---

## 💡 Business Value & Stakeholder Application
* **Target Audience:** Lead Game Designers, Play Design Teams, and Product Managers (e.g., Wizards of the Coast).
* **Problem Solved:** Overpowered cards warp competitive play formats, requiring bans that harm consumer trust. Underpowered cards reduce set engagement.
* **Solution:** This model acts as an **automated baseline pricing tool** for upcoming set development, allowing game designers to mathematically validate card costs, catch power-creep outliers early, and maintain long-term game balance.

---

## 🛠️ Technical Workflow & Architecture

1. **Live Data Ingestion:**
   * Automated REST API extraction from Scryfall returning 1,142 raw JSON objects.
   * Data cleaning, filtering (removing tokens, lands, and uncastable spells), and deduplication down to 647 unique playable cards.

2. **NLP & Feature Engineering (62 Features Total):**
   * Extracted text length and oracle word counts.
   * Custom regex parsing for keyword (kw) mechanics (e.g., `kw_strange_new_worlds`, `kw_beam_me_up`, `kw_federation`, `kw_flying`).
   * Categorical encoding for rarity, color identity flags, and card subtypes.

3. **Machine Learning & Model Tuning:**
   * Trained a `RandomForestRegressor` model to predict continuous mana costs.
   * Evaluated model feature importances to determine cost drivers.
   * Converted output predictions to rounded discrete targets to calculate multi-class classification metrics (Accuracy, Precision, Recall, F1-Score).

* **AI Integration:** Leveraged Google Gemini as a pair-programming and analytical thought partner for debugging Python pipelines, refining NLP feature engineering logic, and structuring executive documentation.

---

## 📈 Key Findings
* **Primary Cost Drivers:** Card color count, artifact typing, toughness, and total oracle text length were the top 4 strongest predictors of mana value.
* **Play Design Adjustments:** The ~48.5% variance from exact matches highlights where human game balance intervention occurs—manually discounting or overcosting cards to account for unquantifiable set-wide synergies and Limited/Draft format needs.

---

## ⚖️ Legal Disclaimer
This project is unofficial Fan Content permitted under the Wizards of the Coast Fan Content Policy. Not approved/endorsed by Wizards. Portions of the materials used are property of Wizards of the Coast. ©Wizards of the Coast LLC.
