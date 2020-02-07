# Play with Habitat demo  
## 1. Download [pointnav_mp3d_v1.zip](https://dl.fbaipublicfiles.com/habitat/data/datasets/pointnav/mp3d/v1/pointnav_mp3d_v1.zip)  

## 2. Demo scripts  
https://github.com/facebookresearch/habitat-api/blob/master/docs/pages/habitat-api-demo.rst  
### (1) Save as .py
Ignore .. code part.  
There are two different functions: Scene semantic annotations and Actions and sensors.  
Better save and try them separately to avoid too many confusing output at the beginning.
### (2) Edit paths in it
```
config =
config.DATASET.DATA_PATH =
config.DATASET.SCENES_DIR =
```
### (3) Run  
```
python [demo script name].py
```

## 3. About episode in demo - Actions and sensors
```
config.DATASET.DATA_PATH = '../data/datasets/pointnav/mp3d/v1/val/val.json.gz'
```
Includes 44 default episodes for validation.  
Change val/val.json.gz to train/train.json.gz to explore more!  
  
```
env.episodes = random.sample(env.episodes, [num])
```
A list, elements in it are randomly chosen [num] episodes from config.DATASET.DATA_PATH  
Object class is NavigationEpisode, for example:  
```
{
"episode_id": "0", 
"scene_id": "data/scene_datasets/mp3d/2azQ1b91cZZ/2azQ1b91cZZ.glb", 
"start_position": [3.967503547668457, 0.12711000442504883, 4.147135257720947], 
"start_rotation": [0, 0.8002702379086439, 0, -0.5996395136393552], 
"info": {"geodesic_distance": 20.11937713623047, "difficulty": "hard"}, 
"goals": [{"position": [20.510929107666016, 0.12711000442504883, 7.4159698486328125], "radius": null}], 
"shortest_paths": null, 
"start_room": null
}
```
  
Load next episode
```
observations = env.reset()
```

Print current scene_id (path of the house.glb)  
```
print("scene:", env.episodes[i].scene_id)
```

## Issues and Tips  
1.  
Install matplotlib
```
conda install -c conda-forge matplotlib  
```
2. 
*ImportError: cannot import name 'd3_40_colors_rgb'*  
**Solution:**  
```
from habitat_sim.utils.common import d3_40_colors_rgb*  
```

3.  
*OSError: cannot write mode RGBA as JPEG*  
**Solution:**  
JPEGs can't represent an alpha channel. Save as other format like PNG.  

4.  
Generate gif from a series of images  
```
brew install ffmpeg
ffmpeg -pattern_type glob -framerate [int] -i '[file prefix]-*.png' [output file name].gif  
```

## Useful Links
Default config  
https://github.com/facebookresearch/habitat-api/blob/master/habitat/config/default.py  
