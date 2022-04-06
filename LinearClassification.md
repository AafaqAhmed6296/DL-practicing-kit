- [Linear Classification | Linear Regression with TF](#linear-classification--linear-regression-with-tf)
  - [Predication](#predication)
  - [Implementaion](#implementaion)
    - [What does Sequential means?](#what-does-sequential-means)
  - [Training / Fitting](#training--fitting)
  - [Plot the value returned by `fit`](#plot-the-value-returned-by-fit)

# Linear Classification | Linear Regression with TF

## Predication

```python
# Predication is rounded value of sigmoid and W-transpose x + b

# Predication = Round(sigmoid(W.T * x + b))
```

## Implementaion

```python
# Implement with Keras Dense Layer
tf.keras.layers.Dense(output_size)
```

> In order to implement this model we actually have two new layer objects in which first one is kind of dummy object. Then create list of those objects and pass that list in to the keras model `Sequential` object.


```python
model = tf.keras.models.Sequential([
    # First we have to create and input object
    # This is essentially just to tell keras the size of your input vector X
    tf.keras.layers.Input(shape=(D,)),

    # Next is dense object,
    # Keras automattically know the input size because that was handle by input object.
    # Only thing that we need to spedify is ouput size and activation function, which is one in this case and sigmoid respectively.

    tf.keras.layers.Dense(1, activation='sigmoid')

])

# We will look at several ways of doing this
```

### What does Sequential means?
> Sequential means each layer in the list we just passed in occures sequentially, or in other words one after the other.


## Training / Fitting

* Need a `cost` / `loss` function: pass it as string as sigmoid was passed in keras layers' **Dense** Object.
  * More incorrect our predications are the larger this cost function becomes.
* `optimizer`: Gradient descent.
  * There are many ways to do this, probably the default for most people is `'adam'`, which means we are specifying keras to use this algorithm.
* `metrics`: pass the list of metrics you want the tensor flow to keep track of, in this case that is the `'accuracy'`


```python
model.compile(
    optimizer='adam',
    lost='binary_crossentropy',
    metrics=['accuracy']
)
```

> Last step is to calling the fit function. It takes two mandatory arugments and other optionals
> * Mandatory
>   * Set of inputs X
>   * Set of targets / Labels Y
> * Optional
>   * `epochs`: As it is iterative technique we need to specify number of iterations, in deep learning we call this epochs, set this based on hit and trail that works for your model.
>   * `validation_data`: This allow us the test our model on set of X, Y data points that are not in the training set, which is very important in **ML**.

```python
# Fit function code

r = model.fit(
    X_train, y_train, 
    validation_data=(X_test, y_test),
    epochs=100
)
```
## Plot the value returned by `fit`

> We can determine the number of epochs with this reutrned data.

```python
plt.plot(r.history['lost'], label='loss')
plt.plot(r.history['val_lost'], label='val_loss')
```