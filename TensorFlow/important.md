❗ Default initializer in a scope is `random_uniform_initializer`. This will cause serious problems with recurrent modules, and as a result lots of `NaN`s will appear. To solve this issue, always select another initializer for recurrent modules, e.g. LSTMs.
```
with tf.variable_scope(scope_name, initializer=tf.random_normal_initializer()):
    cell = tf.contrib.rnn.LayerNormBasicLSTMCell(...)
```
