# LTV-Forecast-Model

[Project Background]
This project forecasted the first and second repurchase rate of three different brands: the oldest brand W and comparatively new brands O and H. With the forecasted repurchase rate of each cohort, we computed the predicted Customer Life Time Value(LTV). We first grouped the customers with the same first purchase month into monthly cohorts. We, then, set 720 days (about 2 years) as a maximum period of retention so that the customers without repurchase in 720 days are regarded to be left. Also, we had two different order types: one-time order and subscription order. With these, we set four different order dynamics: onetime-onetime, onetime-subscription, subscription-subcription, and subscription-onetime. Eventually, this project forecasted the repurchase rate of three different brands in four different order dynamics. The cohorts whose first purchase had passed 720 days are put into training set. Implementing the curve-fitting method, we gradually let the cohorts under 720 days follow the tendency of the training data set. 

Brands:
- W
- O
- H

Order Type:
- OneTime Order
- Subscription Order

Order Dynamics:
- OneTime -> OneTime (OO)
- OneTime -> Subscription (OS)
- Subscription -> Subscription (SS): largest proportion
- Subscription -> OneTime (SO)


[Specific Revision]
Prediction with the first repurchase rate of W which had sufficient data could have stable result. However, the lack of data exceeding 720 days in the brands O and H resulted in such errors as abnormal increase prediction graph slope due to overfitting. To improve such errors, we restructured the data set while maintaining the curve-fitting method. Randomly selecting the cohorts from the first repurchase of W which had the largest volume, we enhanced the size of training set of the others. Also, to reflect the fact that the actual repurchases rapidly decreased after 200-240 days, we divded the total period into two intervals and computed the anticipated value for the first interval. Then, we induced the prediction graph of the second interval to follow the momentum at the last point of the first interval.

[Results]
With such revision, we could compute the LTV based on the anticipated repurchase rate with the highest accuracy of 92% and present the result to the C-Level members.
