### Run the online flow:

modify `soccernet.yaml`: 
- engine -> video
- dataset -> local_video

for visualization:
- added `sn_gamestate/visualization/online_visualization_engine.py`
- added `sn_gamestate/visualization/gamestate.yaml`


### When changing tracklab:

```
uv add ../tracklab
```

Do this so the changes will pick up immediately
```bash
echo "/home/ptgamr/work/sportcontract/vision/soccernet/tracklab" > .venv/lib/python3.9/site-packages/tracklab_dev.pth
```

### opencv-python conflict

When using the `tracklab/engine/video.py`, `cv2.namedWindow` throws error because these two packages of opencv are installed:

- opencv-python
- opencv-python-headless

Have to uninstall both, then reinstall just `opencv-python`

```bash
source .venv/bin/activate

pip uninstall opencv-python opencv-python-headless

pip install opencv-python
```

Not sure how to do this with `uv` yet....


```bash
uv sync --frozen --no-install-package opencv-python-headless
uv run --reinstall-package opencv-python
uv run mim install mmcv==2.0.1
uv add ../tracklab && uv run tracklab -cn soccernet_online
```

### 
