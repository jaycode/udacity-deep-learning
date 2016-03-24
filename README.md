# Deep Learning

This repository is used to store my learning progress in Udacity's Deep Learning course.

## 1. Download and run Docker container

`docker run -dit -v /C_DRIVE/PATH_TO_THIS_DIR:/notebooks -p 8888:8888 tensorflow/tensorflow`

Then open the browser and go to [docker_container_ip]:8888 to verify it is running alright.

## 2. Update jupyter module

Run bash in docker container:

`docker exec -ti [docker_id] bash`

Then update the module:

`pip install -U jupyter`

Then stop jupyter server by running:

`kill $(pgrep jupyter)`

This will actively stop docker container, Then re-start it again:

`docker start [docker_id]`

## 3. Update other modules

This could be in the same step above, but I put on separate point for clarity:

`pip install sklearn`

## 4. Change the indentation to use 2 spaces

Tensorflow uses 2-space indentation instead of the default 4-space. It is annoying to run the code on
this default setting so lets change our ipython notebook's config for indentation:
- Open javascript console.
- Run the following code:
```
var cell = Jupyter.notebook.get_selected_cell();
var config = cell.config;
var patch = {
      CodeCell:{
        cm_config:{indentUnit:2}
      }
    }
config.update(patch)
```

If it returned error `Uncaught TypeError: config.update is not a function(…)` then ipython notebook needs to be updated (see step 2 above), then clear browser's cache.