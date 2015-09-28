To freeze layers in Keras, empty the `params` property of the layer. e.g.:

```python
layer.params = []
```

Also see this: https://github.com/fchollet/keras/pull/727#issuecomment-143395401