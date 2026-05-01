# BrStudentMH: A Reddit Dataset for Mental Health Analysis in the Brazilian University Context

## Introduction

BrStudentMH is a dataset in Portuguese comprising 943 posts and 15,680 comments collected from Brazilian university-related subreddits. It aims to provide a structured resource for research on the mental health of Brazilian university students, taking advantage of the anonymity provided by Reddit, which makes it a space where users discuss sensitive topics without fear of judgment.

---

## Methodology

**Figure 1. Proposed pipeline. (A) Data collection. (B) Mental health categorization and validation. (C) Academic level categorization and validation. (D) Pseudonymization of posts and comments.**

<p align="center">
  <img src="https://github.com/MaiconChavesMarques/BrStudentMH-dataset/blob/main/Images/Pipeline.jpg">
</p>

Data were collected via the Reddit API (PRAW library) from three subreddits, r/USP, r/faculdadeBR, and r/askacademico, using 65 mental health-related keywords, yielding an initial set of 4,811 posts. Large Language Models (DeepSeek V3, ChatGPT 4o, Grok 3, and Gemini 2.5 Pro) were then used to filter and categorize posts by mental health relevance and academic level (applicant, admitted, undergraduate, or graduate), with validation via majority voting and human review for tie-breaking. Finally, the data were pseudonymized using regular expressions and Named Entity Recognition (NER) to mask sensitive information such as names, emails, personal documents, and user mentions.

---

## Data Dictionary

The dataset is provided in `.json` format, in which each field acts as a key that returns the corresponding associated information, organized into two files: **posts** and **comments**. Tables 1 and 2 present the type and a brief description of each field. The relationships between the two files and their corresponding fields can be observed in the entity–relationship diagram below.

Additionally, both keywords and academic level labels are represented in PT-BR, consistent with the language used in post titles, post bodies, and comment texts. The academic level values are: VESTIBULAR, INICIO, GRADUAÇÃO, and POS-GRADUAÇÃO (corresponding to Applicant, Admitted, Undergraduate, and Graduate, respectively).

**Table 1. Data dictionary for the Posts**

| Field | Type | Description |
|---|---|---|
| id | string | Alphanumeric identifier that uniquely identifies a post. |
| title | string | Title of the post created by the user, summarizing the main content or topic. |
| body | string | Textual content of the post, which may include reports, questions, rants, etc. |
| date | date | Post publication date in YYYY-MM-DD format. |
| username | string | Unique identifier of the user who created the post. |
| score | int | Post score based on user interactions (e.g., upvotes and downvotes). |
| academic_level | string | Academic level the post refers to (e.g., Applicant, Admitted, Undergraduate, Graduate). |
| subreddit | string | Name of the subreddit to which the post belongs. |
| keyword | string | Keyword used in the search that retrieved the post. |

**Table 2. Data dictionary for the Comments**

| Field | Type | Description |
|---|---|---|
| id | string | Alphanumeric identifier that uniquely identifies a comment. |
| post_id | string | Identifier of the post to which the comment belongs. |
| parent_id | string | Identifier of the comment being replied to. If null, it indicates a direct reply to the post. |
| username | string | Unique identifier of the user who made the comment. |
| date | date | Comment publication date in YYYY-MM-DD format. |
| body | string | Textual content of the comment, which may include reports, questions, rants, etc. |
| score | int | Comment score based on user interactions (e.g., upvotes and downvotes). |

**Figure 2. Entity Relationship Diagram**

<p align="center">
  <img src="https://github.com/MaiconChavesMarques/BrStudentMH-dataset/blob/main/Images/DER.jpg">
</p>

---

## Applications

The dataset supports research in natural language processing (e.g., mental health disorder detection, sentiment analysis, topic modeling), data mining, and complex network analysis, with a focus on the Brazilian university context. It is intended to contribute both to the development of mental health support tools and to the design of institutional policies aimed at university students.
