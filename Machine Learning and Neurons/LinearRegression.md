
# Linear Regression

## No Activation Function

```python
model = tf.keras.models.Sequential([
    # First we have to create and input object
    # This is essentially just to tell keras the size of your input vector X
    tf.keras.layers.Input(shape=(D,)),

    # Next is dense object,
    # Keras automattically know the input size because that was handle by input object.
    # Only thing that we need to spedify is ouput size 
    tf.keras.layers.Dense(1) # No activation function

])
```

## Stochastic Gradient Descent
```python
model.compile(optimzer=tf.keras.optimizers.SGD(0.001, 0.9), loss='mse')
``` 
> '`mse`': Mean Squared Error \
>  Why no accuracy? For regression it's very unlikely that the prediction will equal the target e.g. target = 1, prediction = 1.001
> * This is good prediction
> * but target == prediction will return false.

## Learning Rate Scheduling 
> Change epoch number, Learn it by practice!

## Moore's law
> Our incomming example is to prove moore's law. \
> Which states: # of transistor / sq inch on integerated circuits doubles approx every 2 years - that's not linear

## Exponential growth

``` 
C = A0 * r ^ t
```
> 
> * `C`: Count variable (Input variable) 
> * `A0`: Initial value of C when t = 0 \
> * `t` : time (input variable, year in our case) \
> * `r` : rate of growth

## Make Exponenetial growth Linear

```
logC = logr * t + logA0
```


