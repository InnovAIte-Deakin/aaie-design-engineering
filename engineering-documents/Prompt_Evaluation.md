**Prompt Evaluation: Full Rubric & Similarity Evaluation (T2 2025)**

The AAIE GenAI Integrated Evaluation System aims to **enhance academic
integrity** by combining **AI content scoring, and prompt-text
similarity analysis**. Students must submit both their **final work,**
and the **AI prompts used** during content generation. If the
**similarity between prompts and final submissions is 40% or more**, the
submission will be flagged for **revision and resubmission**. This
evaluation process ensures **responsible GenAI usage**, originality, and
fair feedback.

**Prompt Details (T2 2025 MVP)**

  --------------------------------------------------------------------------
  **Prompt   **Prompt Text**                            **Use Case**
  ID**                                                  
  ---------- ------------------------------------------ --------------------
  **P001**   Write about why reducing car use in        Feedback generation,
             cities, like in Vauban, Germany, can be a  AI detection, and
             good idea. What are the benefits, and do   similarity
             you think more places should do the same?  evaluation

  **P002**   Discuss how social media affects teenage   Feedback generation,
             mental health.                             AI detection, and
                                                        similarity
                                                        evaluation

  **P003**   Explain why learning a second language is  Feedback generation,
             valuable in today\'s globalized world.     AI detection, and
             Provide examples from your own experiences similarity
             or people you know.                        evaluation
  --------------------------------------------------------------------------

**Evaluation Framework**

**Rubric Criteria (1--3 Scale)**

  ------------------------------------------------------------------------
  **Level**        **Structure**      **Clarity**         **Relevance**
  ---------------- ------------------ ------------------- ----------------
  **1 -- Needs     Disorganized,      Hard to follow,     Off-topic or
  Improvement**    lacks flow         grammar issues      missing key
                                                          points

  **2 --           Partially          Understandable,     Mostly relevant,
  Satisfactory**   organized          some errors         minor gaps

  **3 --           Clear intro, body, Clear, concise,     Fully addresses
  Excellent**      and conclusion     strong grammar      task
  ------------------------------------------------------------------------

**AI Content & Similarity Scoring**

  ------------------------------------------------------------------------
  **Metric**              **Score        **Interpretation**
                          Range**        
  ----------------------- -------------- ---------------------------------
  **AI Content Score**    0--25          Human-Written

                          26--50         Partial Human + AI

                          51--100        Likely AI-Generated

  **Prompt Similarity %** 0--39%         Acceptable

                          ≥40%           Flagged -- Resubmission required
  ------------------------------------------------------------------------

**Prompt Evaluations (Aligned with Prompt Similarity Rule)**

Prompt P001\
*"Write about why reducing car use in cities, like in Vauban, Germany,
can be a good idea. What are the benefits, and do you think more places
should do the same?"*

Student Submission:\
\"Reducing car use can help improve air quality and reduce accidents.
Vauban, Germany, is a good example where car-free living improves
quality of life.\"

GenAI Chat Log (Submitted):

-   Prompt 1: "Write about why reducing car use in cities, like in
    Vauban, Germany, can be a good idea\..."

-   AI Response:\
    "Reducing car use can significantly lower pollution levels, improve
    public spaces, and reduce noise pollution\..."

-   Prompt 2: "Add more on global examples."

-   AI Response:\
    "Cities like Amsterdam and Copenhagen have already implemented
    bike-friendly policies\..."

LLM Evaluation (Visible to Teacher):

-   Rubric Scores:

    -   Structure: 3

    -   Clarity: 2

    -   Relevance: 3

-   AI Content Score: 42 (Partial Human + AI)

-   Prompt Similarity: 38% (Acceptable)

LLM Feedback: Add examples of other cities and a concluding remark on
sustainability.

Teacher Feedback (Visible to Student):\
"Good effort. You clearly explained Vauban's benefits. Add 1--2 global
examples (e.g., Amsterdam) and strengthen your conclusion about why
other cities should follow."

**Prompt P002**

Question:\
*"Discuss how social media affects teenage mental health."*

Student Submission:\
\"Social media connects teenagers but also causes stress, anxiety, and
comparison. Using it moderately can improve mental health.\"

GenAI Chat Log:

-   Prompt 1: Discuss how social media affects teenage mental health.

-   AI Response: \"Social media helps teens connect but is linked to
    anxiety, depression, and low self-esteem.\"

-   Prompt 2: Can you add more negative impacts?

-   AI Response: \"Studies show overuse leads to sleep disruption,
    cyberbullying, and stress.\"

LLM Evaluation (Visible to Teacher):

-   Rubric Scores: Structure: 2, Clarity: 2, Relevance: 3

-   AI Content Score: 60 (Likely AI-Generated)

-   Prompt Similarity: 45% (Flagged -- Resubmission required)

LLM Feedback: Include both positive and negative effects with examples
or statistics for balance.

Teacher Feedback (Visible to Student):\
\"Add more examples and conclude with advice on healthy social media
use.\"

**Prompt P003**

Question:\
*"Explain why learning a second language is valuable in today\'s
globalized world. Provide examples from your own experiences or people
you know."*

Student Submission:\
\"Learning a second language helps with cultural understanding, career
opportunities, and communication. My friend benefited by finding a
global job.\"

GenAI Chat Log:

-   Prompt 1: Explain why learning a second language is valuable in
    today\'s globalized world.

-   AI Response: \"It opens career opportunities and fosters
    intercultural communication.\"

-   Prompt 2: Add personal examples.

-   AI Response: \"For instance, someone I know got a job abroad due to
    their language skills.\"

LLM Evaluation (Visible to Teacher):

-   Rubric Scores: Structure: 3, Clarity: 3, Relevance: 3

-   AI Content Score: 18 (Human-Written)

-   Prompt Similarity: 32% (Acceptable)

LLM Feedback: Add more real-world benefits and a strong conclusion on
globalization.

Teacher Feedback (Visible to Student):\
\"Well-written and relevant. Expand with examples of global companies
valuing bilingual skills.\"

**Rubric & Similarity Summary Table**

  ------------------------------------------------------------------------------------------
  **Prompt   **Structure**   **Clarity**   **Relevance**   **AI Content     **Prompt
  ID**                                                     Score**          Similarity**
  ---------- --------------- ------------- --------------- ---------------- ----------------
  **P001**   3               2             3               42 (Partial AI)  38% (Acceptable)

  **P002**   2               2             3               60 (Likely AI)   45% (Flagged)

  **P003**   3               3             3               18 (Human)       32% (Acceptable)
  ------------------------------------------------------------------------------------------
