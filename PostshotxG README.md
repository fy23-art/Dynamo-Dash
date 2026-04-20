# PostshotxG
Post-Shot Expected Goals model using agent-imputed tracking data with the Hosuton Dynamo F.C.

Summary and Goal: 

One of the most well-known and widely used developments in soccer analytics is Expected Goals (xG), which measures the likelihood that a shot will be scored based on other similar shots taken from the same location and in a similar context (body part, phase of play, location of the goalkeeper, etc.). 

Post-Shot xG is a similar idea, with the key difference that instead of evaluating the likelihood of a shot ending in a goal based on the information at the time of the shot, we also look at important information after the shot, like the end-location of the shot on the goal and the velocity of the shot. Post-Shot Expected Goals is highly useful for evaluating goalkeepers by comparing the number of goals they concede to the number of post-shot expected goals they face, and may also be useful for evaluating a player’s finishing ability in a more accurate manner than just looking at goals scored. 

The problem that the industry faces is that most PSxG models are very “noisy”, and do not give precise readings on the likelihood that a shot would end in a goal. This limits our ability to make accurate inferences using these metrics; as an example, using StatsBomb’s industry-leading PSxG model, we need goalkeepers to face around 250 shots before we can trust their PSxG - Goals conceded value to stabilize across the next 250 shot sample. Assuming 5 shots on target faced per match, this would mean we need at least 50 games played to evaluate a goalkeeper for an even somewhat reliable sense of their shot stopping ability. Using Wyscout’s less-accurate model, this number is even higher. 

SRC has developed a new, one-of-a-kind dataset build on top of Wyscout’s event data that mimics tracking data by inferring where each player on the field would be in an average situation similar to the current one. Using this new data, we hope to be able to hugely improve on Wyscout’s PSxG model, and hope to beat StatsBomb’s model as well. 

Defining Models:

- Expected Goals (xG): prrobability of a shot resulting in goal (0-1) from past shots of similar characteristics
- Post-Shot xG (PSxG): calculated after a shot has been taken, assessing goalkeeper shot-stopping ability, insight to finishing ability

Project Aim: 

Using agent-imputed event data from Wyscout, we will build a proprietary Post-Shot Expected Goals (xG) model that outperforms the model provided by Wyscout, and performs similarly or outperforms StatsBomb’s model as well. 
- More logical predictions for shots on the event level (subjective, based on video analysis)
- More stability in small-to-moderate sample sizes on the player level
- Closer predictions to StatsBomb’s PSxG model  

Features considered:

Distance from goal, Angle to goal, Defenders in the way, Goalkeeper positioning, Player assisting (yes/no, where pass came from), Speed of shot, Deflection, Shot placement, phase of play (Controlled Play, Tradition, Set Piece), Chance creation type (set piece, cross, cutback)

Intended Results & Impact:

The new model will be used as the primary PSxG model for Wyscout, which is the main data source for multiple clients. The model will have implications for player evaluation, match reports, research projects, and more. 

Evaluation Methods:

- Area Under ROC Curve (AUROC)
- Brier Score (Calibration error)
- Mean Absolute Error, Mean Absolute Percentage Error, Mean Squared Error
- Logistic Regression
- XGBoost
- Neural Network / LSTM 

