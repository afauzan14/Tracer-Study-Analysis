# Alumni Tracer Study Analytics & Career Segmentation Using K-Prototypes

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Clustering](https://img.shields.io/badge/Algorithm-K--Prototypes-blue?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Higher%20Education%20Analytics-success?style=for-the-badge)

---

## Project Overview & Business Understanding

A **Graduate Tracer Study** is an essential instrument for higher education institutions to evaluate educational quality, assess curriculum relevance against job market demands, and fulfill institutional **Key Performance Indicators (KPIs)**. However, alumni survey datasets typically consist of **mixed data types** containing unstructured free-text responses, non-standardized income formats, and varying survey completion patterns.

This project analyzes tracer study survey data from the Faculty of Science and Technology (FST) at UIN Syarif Hidayatullah Jakarta across 7 academic departments: *Informatics, Agribusiness, Biology, Chemistry, Physics, Mathematics, and Mining Engineering*.

The primary objectives of this study are:
1. **Survey Data Hygiene & Feature Engineering:** Resolving inconsistencies in unstructured text inputs and deriving key analytical variables such as job search duration, study completion period, and employment status.
2. **Curriculum & Industry Alignment Evaluation:** Assessing vertical curriculum alignment (skills acquired vs. industry demands) and horizontal relevance (major vs. field of work).
3. **Alumni Segmentation via Machine Learning:** Developing an unsupervised clustering model utilizing **K-Prototypes** to simultaneously process numerical and categorical alumni attributes.
4. **Data-Driven Institutional Policy Recommendations:** Delivering actionable strategies for academic faculties to accelerate graduation rates, optimize graduate employability, and support postgraduate research pathways.

---

## Methodology & Data Processing

1. **Data Preprocessing & Text Normalization:**
   * **Text Anomaly Standardization:** Standardized free-text responses regarding employment wait times, monthly income brackets, postgraduate university names, and department labeling.
   * **Outlier & Duplicate Filtering:** Removed duplicate submissions from survey respondents and treated extreme anomalies in study duration and waiting periods.
2. **Feature Engineering:**
   * `study_duration`: Derived total study completion period (years) from enrollment and graduation timestamps.
   * `employment_status`: Consolidated into standard classes (*Employed, Unemployed / Job Seeking, Pursuing Higher Degree, Entrepreneur*).
   * Encoded ordinal feedback regarding curriculum alignment and field-of-study match onto a standardized 1–5 scale.
3. **Machine Learning: K-Prototypes Clustering:**
   * **K-Prototypes** was implemented via the `kmodes` library to handle mixed data types without loss of information.
   * Numerical distances were computed using *Euclidean distance*, while categorical dissimilarities were evaluated using *matching dissimilarity*.
   * An optimal cluster count of **$k = 3$** was established to deliver actionable and interpretable alumni personas.

---

## Key Findings

### 1. Departmental Comparison: Employability & Curriculum Alignment

| Academic Department | Average Study Duration | Job Search Duration (Wait Time) | Curriculum & Field Relevance |
| :--- | :--- | :--- | :--- |
| **Informatics** | Efficient (4.0 – 4.5 Years) | Rapid (< 3 months); highest direct workforce absorption | High; strong technical alignment with high-demand tech roles |
| **Mathematics & Physics** | 4.0 – 5.0 Years | Short to moderate (3 – 6 months); prominent in analytical & education sectors | Strong synergy in data science, actuarial, and computational domains |
| **Biology & Chemistry** | 4.0 – 5.0 Years | Moderate; highest proportion pursuing postgraduate studies (Master's / Ph.D.) | Highly relevant to research laboratories, QA/QC, and academic paths |
| **Mining Engineering** | 4.5 – 5.5 Years | Strong absorption within natural resources and energy sectors | High domain-specific skill utilization with competitive starting salaries |
| **Agribusiness** | Longer (> 5.0 Years) | Extended wait time; larger pool of active job seekers | Broad corporate & agritech opportunities, requiring enhanced portfolio preparation |

---

### 2. Alumni Segmentation Personas (K-Prototypes, $k = 3$)

| Cluster Persona | Key Defining Characteristics | Dominant Academic Programs | Employment Status & Transition Speed |
| :--- | :--- | :--- | :--- |
| **Cluster 1: Rapid Workforce Absorption** | • Graduated 2023 onwards<br>• Highly efficient study duration<br>• High curriculum alignment ratings (Scores 4–5) | Informatics, Mathematics, Biology | • **> 90% Actively Employed**<br>• Job search duration: **< 3 months**<br>• High concentration in private corporate sector |
| **Cluster 2: Adaptive Transition (Balanced)** | • Dominated by mid-year 2024 graduates<br>• Preference for corporate roles over entrepreneurship | Agribusiness, Biology, Informatics | • **Balanced distribution** between employed alumni and candidates actively undergoing hiring pipelines<br>• Wait time: 0–6 months |
| **Cluster 3: Early Career Exploration** | • Dominated by late-2024 fresh graduates<br>• Noticeable proportion preparing for postgraduate study | Agribusiness, Biology, Mathematics | • **Predominantly job seekers** in the initial post-graduation transition period<br>• Require targeted career placement support |

---

## Strategic Recommendations for Academic Faculties

### 1. Targeted Career Acceleration Programs
* **Industry Partnerships & Campus Hiring:** Establish dedicated career placement pipelines for departments with longer transition times (e.g., Agribusiness) through corporate networking, verified digital skill bootcamps, and certified final-year internships.
* **Incubator-Based Entrepreneurship:** Data indicates a low rate of entrepreneurship among graduates. Transition traditional business lectures into project-based incubator programs offering seed funding mentorship.

### 2. Continuous Curriculum-Industry Alignment
* Maintain dynamic, agile curricula for high-employability programs (Informatics and Mathematics), while embedding essential soft skills (executive communication, English proficiency, problem-solving) across all sciences to maximize interview success.

### 3. Postgraduate Advisory & Research Mentorship
* Establish an advisory desk for natural science graduates (Biology, Chemistry, Physics) who demonstrate high academic aspirations, offering dedicated support for scholarship applications (e.g., LPDP), research proposal preparation, and indexed scientific publications.
