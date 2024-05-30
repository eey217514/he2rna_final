Note that singularity has been renamed to apptainer. You can access the docs here: https://apptainer.org/docs/user/1.2/index.html

1) I've built a container here that you can test. You can access it and its definition file here: /charonfs/scratch/users/astar/gis/yeohtg/containers/tf

If you need to install more libraries, edit the tf.def file and rebuild the container using
```
singularity build tf.sif tf.def
```

2) Check that tensorflow is able to use the gpu. Note that `--nv` is needed so that singularity can access the gpus. 
```
singularity run --nv ~/containers/tf.sif python -c "import tensorflow as tf; print(tf.test.is_gpu_available())"
```

3) Check that imports work for scripts
```
singularity run --nv ~/containers/tf.sif python extract_tile_features.py -h
singularity run --nv ~/containers/tf.sif python extract_tile_features_from_slides.py -h
```
