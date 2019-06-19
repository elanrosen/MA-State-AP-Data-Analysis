## Overview
Used readily availible data from the Massachusettes Department of Education(DOE) on the AP performance of high schools(district data was also availible), to reach conclusions on a schools relative performance.
### Resources
[Massachusettes AP Scoring Data from DOE](http://profiles.doe.mass.edu/statereport/ap.aspx)

[2018 AP Exam Scoring Distributions](https://www.totalregistration.net/AP-Exam-Registration-Service/AP-Exam-Score-Distributions.php?year=2018) While these numbers are not directly from *The College Board*, the statistics are valid. You can check if you want. These numbers were in an easier to use format.

### Preface
This was a very earlier python data science project of mine, so the analytical and programming practices utilized are at best sub-par. I was more focused on reaching the results than using or learning proper python and pandas programming methods. I plan to eventually optimize the whole program.

In addition, certain aspects of the analysis have instances of bias. While measures were taken for courses and scores to be weighted in an objective matter, the data is not definitive. In this project especially, difficulty existed in determing the value of courses and scores as too generalize them as all equal would be too great of a simplification to reach strong results, but to make the analysis to nuanced would introduce too much subjectivity on the part of myself. In this project, I attempt to strike a balance between these two issues.

The grammar in this Readme may not be so good. This was quickly written up in a text editor.

### Background
The reason this project was created was my current disfatistation with current high school ranking methodology. While current ranking methodology does a decent job at figuring out which schools are overall "good", they are inadequate at determing which schools are great. Current methodolgies only look at very simplified data points like AP participation and pass rates.
AP participation can easily be increased through easy classes, district fee-waivers, and other methods. Pass rates are increadibly decieving due to the stark rigor differences in the AP course providings. A school could easily have an inflated pass rate due to easier AP course offerings ie AP Enviromental Science. In addition, many exams require a score of less than 60% correct to pass, which in my opinion and experience is far too low of a bar to be deemed a success.

My method of finding the overall "greatness" independently weights each subject based on the nationwide scoring satistics and only uses only scores of 4 and 5. Then this performance was divided by total enrollement to gauge the overall sucess.

### Weighting of Scores

Each AP exam had a designated 5constant and 4constant (which are really just coefficients) for the # of scores per school to be multiplied by. These constants would serve as a way to weight which scores would be considered more impressive in these rankings, so that scores in classes like AP Biology with a 6% 5-rate are weighted more than for instance AP Microeconomics with a 20% 5-rate. **Foreign Language scores were fully excluded from this project due to the extremely high 5-rates(likely due to a large amount of native-speaking test-takers). Some low enrollement science classes were also excluded, as very few students had acess to them**

The general formula for the 5constant was:

![Equation](https://raw.githubusercontent.com/elanrosen/MA-State-AP-Data-Analysis/master/Photos/5constant_formula.gif)

The 5rate would be the percent of students scoring in the 5 range. The 4 constant formula was:

![Equation](https://raw.githubusercontent.com/elanrosen/MA-State-AP-Data-Analysis/master/Photos/4constant_formula.gif)

The objectivity of this method of weigting does lead to some unfair weightings of courses where some easier classes recieve similar weighting to known hard courses like AP Biology being weighted the same as AP Enviromental Science. However, for the most part courses recieved an adequate rating of their difficulty in these weightings.

These constants are visible in the [constants.xlsx](https://github.com/elanrosen/MA-State-AP-Data-Analysis/blob/master/constants.xlsx) file.

### Further Calculations

"Indexes" refers to the cumulative total of weighted averages for different exams for a particular subject or subject area. With the AP Index indicating overall performance.

The BiologyIndex would be equal to ((# of students who scored 5)(5constant) + (# of students who scored 4)(4constant))/(total enrollement)

The MathIndex would be equal to ABCalcIndex + BCCalcIndex

The APIndex would be equal to ScienceIndex + MathIndex + ScienceIndex + EnglishIndex + HistoryIndex

Rankings based off the APIndex:
![APIndex Rankings](https://raw.githubusercontent.com/elanrosen/MA-State-AP-Data-Analysis/master/Photos/APIndexRankings.png)

(At the time I couldn't figure out how to consistently convert school ID to High School Name)
But if you are wondering, 350560 is Boston Latin and the next three are Hopkinton, Lexington, and Belmont

### Future Plans

Ideally, I go back and fix the code and add in some for loops and better pandas usuage.

Beyond that, I have been musing about making a full on program that would allow one to via a GUI compare different years of performance of a selected school.

I also would like to revisit some of the weighting methodology to better reward difficult scores and negate the benefits of easily obtained ones.
