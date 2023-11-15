<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

## Table of Contents
- [Overview](#overview)
- [Resources](#resources)
- [Preface](#preface)
- [Background](#background)
- [Methodology for Score Weighting](#methodology-for-score-weighting)
- [Advanced Metrics for Comprehensive Analysis](#advanced-metrics-for-comprehensive-analysis)
- [Future Plans](#future-plans)

## Overview
This project harnesses publicly available data from the Massachusetts Department of Education to analyze and draw conclusions about the relative performance of high schools within the state. By examining Advanced Placement (AP) performance data, it offers a nuanced view of school effectiveness.

### Resources
- [Massachusetts AP Scoring Data from DOE](http://profiles.doe.mass.edu/statereport/ap.aspx): This official dataset provides a comprehensive overview of AP performance across Massachusetts schools.
- [2018 AP Exam Scoring Distributions](https://www.totalregistration.net/AP-Exam-Registration-Service/AP-Exam-Score-Distributions.php?year=2018): These statistics, while not sourced directly from The College Board, are nonetheless a reliable indicator of national performance benchmarks.

### Preface
As an early foray into Python data science, this analysis prioritizes substantive insights over technical sophistication. The primary objective was to derive meaningful conclusions rather than perfecting programming techniques using Python and its libraries. Admittedly, the approach may not be devoid of bias, and the complexity of evaluating the true academic value of AP courses and scores presents a challenge. This project endeavors to balance between oversimplification and excessive subjectivity in its analysis.

### Background
The impetus for this study is a dissatisfaction with prevailing high school ranking systems, which often fail to differentiate between the good and the truly exceptional. Traditional metrics such as AP participation and pass rates do not adequately reflect school quality due to their susceptibility to manipulation and their failure to account for the variable difficulty across AP courses. For example, a school could inflate its pass rates by offering easier AP courses, such as Environmental Science, whereas more challenging subjects may present a truer measure of academic rigor.

To address this, the project introduces a novel metric of "greatness" that weights AP scores of 4 and 5 according to their national distribution, thus acknowledging the varying difficulty levels of exams. This metric is then normalized by the total student enrollment to provide a more accurate representation of school performance.

### Methodology for Score Weighting

The analysis incorporates a tailored scoring system, assigning unique multipliers—termed as '5constant' and '4constant'—to the quantity of AP exam scores achieved by each school. These multipliers function as a means to calibrate the significance of scores within the overall rankings. More substantial weight is accorded to scores attained in courses where high achievement is less common, exemplified by a 6% national 5-rate in AP Biology, as opposed to a 20% in AP Microeconomics.

An intentional omission from this analysis is the scores from Foreign Language AP exams, attributed to disproportionately high 5-rates, which likely stem from native speakers taking these exams. Additionally, certain science courses with minimal enrollment are excluded to avoid skewing results due to limited data availability.

The established formulae for the 5constant and 4constant are as follows:

![Equation for 5constant](https://raw.githubusercontent.com/elanrosen/MA-State-AP-Data-Analysis/master/Photos/5constant_formula.gif)

The '5rate' represents the percentage of students nationally scoring a 5 on the exam. The formula for the 4constant is similarly structured:

![Equation for 4constant](https://raw.githubusercontent.com/elanrosen/MA-State-AP-Data-Analysis/master/Photos/4constant_formula.gif)

While striving for objectivity, this method occasionally results in comparable weightings for exams of varying difficulty. For instance, an easier course might inadvertently receive a weighting similar to a more rigorous one. Nevertheless, the system generally assigns a reflective difficulty rating to each course. The detailed coefficients for each AP exam can be reviewed in the [constants.xlsx](https://github.com/elanrosen/MA-State-AP-Data-Analysis/blob/master/constants.xlsx) document.

### Advanced Metrics for Comprehensive Analysis

In the pursuit of a more granular understanding of academic prowess, the project utilizes a series of "Indexes." These indexes are essentially composite scores representing the weighted achievements across different AP exams within various disciplines.

- **Biology Index**: This metric calculates the prowess in biology by combining the weighted numbers of students who earned scores of 5 and 4, adjusted by the total enrollment. It's a formula that appreciates higher achievement in the subject by applying the predetermined constants:
  
<span>
  Biology Index = \(\frac{(\text{\# of 5s} \times \text{5constant}) + (\text{\# of 4s} \times \text{4constant})}{\text{total enrollment}}\)
</span>

- **Math Index**: A summative indicator of mathematical achievement, the Math Index is the sum of the indexes for Calculus AB and Calculus BC, reflecting the school's strength in advanced mathematical education.

- **AP Index**: Serving as the overarching measure of AP success, the AP Index is the sum of indexes for all subject areas. It synthesizes performance across science, mathematics, English, and history to yield a comprehensive score:
  
<span>
  AP Index = \(\text{Science Index} + \text{Math Index} + \text{English Index} + \text{History Index}\)
</span>

The rankings derived from the AP Index provide a leaderboard of scholastic excellence. The visualization of these rankings, while currently keyed to school IDs, offers an insightful snapshot of where schools stand in fostering advanced academic achievement.

For context, school ID 350560 corresponds to the prestigious Boston Latin School, followed closely by Hopkinton High, Lexington High, and Belmont High — each known for their robust AP programs.

In future iterations, enhancing the clarity of the data by mapping school IDs to their respective names will be a priority, thereby making the results more accessible and informative for all stakeholders.

### Future Plans

- **Code Optimization**: Refine the codebase for efficiency, incorporating for loops and advanced Pandas techniques.
- **GUI Application**: Develop a user-friendly GUI to enable cross-year performance analysis for individual schools.
- **Weighting Reassessment**: Reassess scoring weights to more accurately reflect AP exam rigor and adjust for course difficulty.
