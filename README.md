# CarND-Controls-PID (Write up from Karab)

## Desribe PID Controller
## P - Proportional
The directly proportional feedback to the Error/Diviation. Higher the P ratio, the faster the response.
When I tune the P larger, it can make efficient response to the change of road lane. 
But if the value is too large, it will create oscilliation, which cannot be reduce even for adding large D.

## D - derivative
To prevent the steering become sharp and over-adjusted, which causing oscillation around the target.
It is good to help the case of oscillation. However, too large of it would cause the failure of turning round.

## I - Integral
For auto calibration on the shifted control error and measurement error. However, if it is tuned too large, it will keep oscillating too. 
In the process of this case, the Integral part can even be vanished.


## Method of hyper-parameter tuning
The way i decide for the tuning is the manual process and the number of parameter is small and road is realtively normal.

| Trial# | Parameters(P, I, D) | Remark |
|: ------ |:----------------:| -----------------------:|
| 1 | (0.2, 0.004, 3.000) | It oscillates too much. And will be out of the track sometime |
|2| (0.1, 0.004, 3.000) | Tried Reduce P for less oscilliation. But the car even out of track
|3| (0.3, 0.004, 3.000) | It maintains on Road for a while. Also seems a bit off the road, reduce D for over react |
|4| (0.3, 0.004, 2.500) | Osciliate a lot after some time, Tune down the I paramter first |
|5| (0.3, 0.001, 2.500)| Can Fisish the track, But too slow to adopt the turn change.|
|6| (0.33, 0.0011, 2.500) | Get better in turning curve but oscilliate too obviously.|
|7| (0.33, 0.0011, 2.750) | Add D to reduce oscilliation|
|8| (0.33, 0.000, 2.750) | Remove the Integral part to keep it even less strange oscilliation|
|9| (0.33, 0.000, 5) | Add D to 5 and the oscilliation is much better. Decide to stop tunning. |
