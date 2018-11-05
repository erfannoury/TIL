Distributed training (with `TF_CONFIG`) will only start for the Estimator if `tf.estimator.train_and_evaluate` is called. It does not work with `Estimator(...).train`.
