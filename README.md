# MLB-Regression-Analysis
Used MLB data to create a linear regression model to figure out which features correlate with team success.

Data Source: https://www.baseball-reference.com/leagues/majors/2024.shtml

# Data Loading & Cleaning

Converted files from site into csv files using Excel & Pytho
cleaned_team_war.csv

combined_teams.csv

team_fields.csv

team_stan_bat.csv

team_stan_pitch.csv

wins_above_avg.csv

# Exploratory Data Analysis
 --BenHuynhEDA.RMD & BenHuynhEDA.html

 Familiarized myself with data. Looked at distribution statistics, shape, & correlation.

Examples:

 <img width="1066" height="843" alt="image" src="https://github.com/user-attachments/assets/a6831955-c98a-4a61-8baa-eb960a43ca64" />

 <img width="980" height="795" alt="image" src="https://github.com/user-attachments/assets/4252decb-df3f-4a40-9abe-9de3f98a8865" />

<img width="1055" height="844" alt="image" src="https://github.com/user-attachments/assets/732ec9e3-fc2c-4051-b360-cb43ab9f03d1" />

<img width="1007" height="464" alt="image" src="https://github.com/user-attachments/assets/e0298ff2-b132-4579-a9ad-f3598014e41f" />

<img width="1093" height="484" alt="image" src="https://github.com/user-attachments/assets/9e63651c-6e11-4362-89aa-355781625ac7" />

Conclusion pertaining to win correlation:

Positive Relationship~ Strong linear:DefEff, Non-P, OPS+, SV, Wins_Abv_Avg Moderate Linear:BB_Bat, DH, ERA+, HR_Bat, OF(ALL), OPS, R/G, R_Bat, RBI, SLG, SO_P, SO9, TB, tSho Weak Linear: #Fld, 1b_pos, 3b_pos, BA, C, Fld%, LF, OBP, PA, PH, RF, SP

Negative Relationship~ Strong Linear: H9, HitAllow, Rk, WHIP Moderate Linear: ER, ERA, LOB_P, Weak Linear:BB_P, BB9, BF, E, FIP, HR_P, IBB_P, Inn, SH, SO/W

Not Pos or Neg but Linear:#Bat, #P, 2b_Bat, A, HBP_P, IBB_BAT, IP, SS, WP No Relationship:2b_pos, 3b_BAt, AB, AllP, BatAge, BK, CF, CG_F, CS, cSho, GDP, H_Bats, HBP_Bat, HR9, PAge, PO, Rdrs, Rdrs/yr, Rgood, RP, Rtot, Rtot/yr, SB, SF, SO_Bat

(Quadratic or Parabola) Stong Curvilinear: Moderate CurvilinearL:LOB_BAT Weak Curvilinear: Ch, DP

Log Relationship ~ Negative - Strong: Moderate:R_P, RA/G Weak:

Positive - Strong: Moderate: Weak:

Nothing too suprising, only noticeable observation is that there are more, stronger or moderate linear relationships between defensive state(pitching and fielding) and wins than there are offensive stats and wins.

# Model Building

Model_Building.html
Model_Building2.html
Final_Model.html

Investigated features and model performance, then took those findings to tune another model and repeat. Looked at analytics for multicollinearity, interaction, and other variables that would prevent the model from being ineffective or not generalizing well.

Final model Conclusion:

(W ~ OPS + ERA + HR_Bat + Rdrs + FIP + DH_centered + DH_c2

train R^2: 0.9268 test R^2 : 0.7439 RMSE: 6.5602

The test R^2 r^2 = 0.7439 means the model generalizes reasonably well, indicating a moderate predictive stability. The RMSE is fairly low also relative to the 162 games games played in a single baseball season.

The final model: (W ~ OPS + ERA + HR_Bat + Rdrs + FIP + DH_centered + DH_c2. The variables all play a crucial roll in development of the model. I believe the most influential step was the initial single order term selection during EDA. Although DH is a significant polynomial term, I don’t think it was the most influential. I did drop some predictors initially, as in the context of the data they were redundant but besidses, that, there were not too many significant decisions that didn’t come from the initial EDA.

Balancing fit vs interpretability was not a challenge with my model. The only variable that could provided a challenge was the DH or designated hitter variable. In order to apply it to our linear model there was no need for a transformation or anything too complicated, just squaring and centering the variable. I believe this doesn’t influence the interpretability at all. Because of this, I could really focus on fit and that is reflected in the model performance. Would get rid of DH to make model generalize better but for assignment parameters, my model is as shown.


