# Bundesliga-prediction-ML
## Pipline 
### Daten understanding
- Quelle: Historical Football Results and Betting Odds Data(https://www.football-data.co.uk/data.php)
- Row data from Bundesliga in session 2017-2021 ( Feature explanation see /data/Notes for football data)
- Basic backroud:
    - In Bundeslig matches in a year:
    - 306 matches 
    - 34 'Spieltag'(week)
    - 9 matches one week (full 18 teams in matching) 

### Feature engineering
- Initally select 5 basic features:
    - 'HomeTeam': home team name
    - 'AwayTeam': away team name
    - 'FTHG': Full Time Home Team Goals 
    - 'FTAG': Full Time Away Team Goals
    - 'FTR': Full Time Result (H=Home Win, D=Draw, A=Away Win)
- based on these features created intermediate features: 
    - HTGD: Home team goals difference (Calculate the cumulative goal difference per team per week)
    - ATGD: Away team goals difference
    - HTP: Home team cumulative points (Cumulative points for each team{ win: 3p; draw: 1p; lose: 0p})
    - ATP: Away team cumulative points
    - HM1,HM2,HM3 represents results of last 1/2/3 matches from home team(W:'win', D:'draw', L:'lose')
    - AM1,AM2,AM3 represents results of last 1/2/3 matches from away team
    - MW: in which week(Spieltag)
    - Get mean value divided by 'week', then override HTGD, ATGD ,HTP and ATP 
- freatures sorting:
    - drop the intermediate features, drop first 3 weeks data(not enough information)
    - drop'HTP','ATP'(which are highly correlated with HTGD, ATGD) 
    - dummy encodeing
- got final features: 'HTGD', 'ATGD', 'HM1_D', 'HM1_L', 'HM1_W', 'AM1_D', 'AM1_L', 'AM1_W', 'HM2_D', 'HM2_L', 'HM2_W', 'AM2_D', 'AM2_L', 'AM2_W', 'HM3_D', 'HM3_L', 'HM3_W', 'AM3_D', 'AM3_L', 'AM3_W'

### Model training and selecting
- Evaluate following models and compare the apperance 
    - Random Forests Model
    - XGBoosting Model
    - Support Vector Machines
    - Gradient Boosting Classifier
    - K-nearest neighbors
    - Gaussian Naive Bayes
    - Logistic Regression

- got the sore comparations:

### Model parameter tuning
- use grid-search for parameter selecting


### Wrap-up and reflections
<table class=MsoTableGrid border=1 cellspacing=0 cellpadding=0
 style='border-collapse:collapse;border:none;mso-border-alt:solid windowtext .5pt;
 mso-yfti-tbllook:1184;mso-padding-alt:0cm 5.4pt 0cm 5.4pt'>
 <tr style='mso-yfti-irow:0;mso-yfti-firstrow:yes'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US><o:p>&nbsp;</o:p></span></p>
  </td>
  <td width=183 colspan=2 valign=top style='width:136.95pt;border:solid windowtext 1.0pt;
  border-left:none;mso-border-left-alt:solid windowtext .5pt;mso-border-alt:
  solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US>Train-dataset</span></p>
  </td>
  <td width=158 colspan=2 valign=top style='width:118.5pt;border:solid windowtext 1.0pt;
  border-left:none;mso-border-left-alt:solid windowtext .5pt;mso-border-alt:
  solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US>Test-dataset</span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:1'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>Model</span></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>F1<o:p></o:p></span></b></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>Acc<o:p></o:p></span></b></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>F1<o:p></o:p></span></b></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>Acc<o:p></o:p></span></b></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:2'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>Random Forests<o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=DE style='mso-ansi-language:DE'>0.9988<o:p></o:p></span></b></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>0.9990</span></b><b><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></b></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5172</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5990</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:3'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span class=SpellE><b><span lang=EN-US>XGBoosting</span></b></span><b><span
  lang=EN-US><o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>0.9905</span></b><b><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></b></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>0.9918</span></b><b><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></b></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5255</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5776</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:4'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>SVM<o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5066</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.6527</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.4952</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>0.6253</span></b><b><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></b></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:5'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>Gradient Boosting <o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.7345</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.7807</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>0.5395</span></b><b><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></b></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5967</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:6'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span class=SpellE><b><span lang=EN-US>Knn</span></b></span><b><span
  lang=EN-US><o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.7226</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.7664</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.4057</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5036</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:7'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>Gaussian Naive Bayes<o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5543</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.6260</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5323</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5847</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
 </tr>
 <tr style='mso-yfti-irow:8;mso-yfti-lastrow:yes'>
  <td width=170 valign=top style='width:127.35pt;border:solid windowtext 1.0pt;
  border-top:none;mso-border-top-alt:solid windowtext .5pt;mso-border-alt:solid windowtext .5pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=EN-US>Logistic Regression<o:p></o:p></span></b></p>
  </td>
  <td width=94 valign=top style='width:70.85pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.5369</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=88 valign=top style='width:66.1pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.6465</span><span lang=DE
  style='mso-ansi-language:DE'><o:p></o:p></span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='tab-stops:31.55pt'><span lang=EN-US>0.5291</span></p>
  </td>
  <td width=79 valign=top style='width:59.25pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  mso-border-top-alt:solid windowtext .5pt;mso-border-left-alt:solid windowtext .5pt;
  mso-border-alt:solid windowtext .5pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>0.6134</span></p>
  </td>
 </tr>
</table>

- Features in Datasets are rouoghly divided 3 parts(Results data, Match Statistics, Betting odds data)
    - features now in Pipline are mainly Results-data based. 
- Evaluation from models shows best Performance:
    - Baseline: If predict the winner is Home-team, the accuracy is about  0.43921568627450985
    - Random Forests/XGBoosting on Train-data (obviously overfitting)
        - reason: not enough features? 
    - SVM and Logistic-gregression shows better on test-data
- Next step?
    - create more features from Match Statistics
    - consider participating players and their health information (Information from social media/tweets?)
    - consider relevant news information
    - consider odds from betting data
