# The Wolf-Sheep-Grass model

This is a Python reimplementation of NetLogo's Wolf-Sheep-Grass model https://ccl.northwestern.edu/netlogo/models/WolfSheepPredation

Install via 
```commandline
pip install -e .
```
within this directory. (The "editable" `-e` flag may be omitted if you do not plan on changing the model.)

Typical usage can be viewed in `wolves-sheep-grass.py`. e.g. the model can be instantiated with parameters:
```python
from wolf_sheep_grass import WolfSheepGrassModel

model = WolfSheepGrassModel(
    GRID_WIDTH=...,
    GRID_HEIGHT=...,
    INIT_WOLVES=...,
    WOLF_GAIN_FROM_FOOD=...,
    WOLF_REPRODUCE=...,
    INIT_SHEEP=...,
    SHEEP_GAIN_FROM_FOOD=...,
    SHEEP_REPRODUCE=...,
    INIT_GRASS_PROPORTION=...,
    GRASS_REGROWTH_TIME=...,
)
```
The model is advanced forward in time using `model.time_step()`. Classic usage will find `model.num_wolves`,`model.num_sheep`, and `sum(model.grass)` interesting. More advanced usage might look at `model.grass` directly which is a 2d boolean array indicating grass presence or one of the agent arrays: 
* `model.wolf_pos` / `model.sheep_pos`
* `model.wolf_dir` / `model.sheep_dir`
* `model.wolf_energy` / `model.sheep_energy`
each of which should be masked by the boolean arrays `model.wolf_alive` or `model.sheep_alive`.
