# Omni-MOT Dataset Recorder
> This is the repository of recording [Omni-MOT]() dataset. Its functions include: 
>
> - Camera Operations: Move forward backward, pitch up down, roll left right, yaw left right
> - Save camera parameters
> - Calculate the ground truth data for multiple object tracking (i.e. 3D bounding boxes, 2D bounding boxes, Visibility)
> - Save Videos and Ground Truth

## Requirement
- CARLA 0.9.4, refer to [[CARLA Docs]](https://carla.readthedocs.io/en/latest/getting_started/)

- \>= Ubuntu 16.0

- clone this repository into your local disk

  ```shell
  git clone https://github.com/shijieS/OMOTDRecorder.git
  ```

- Install the required packages

  ```shell
  cd <this repository>
  pip install -r requirement.txt
  ```

- make sure all the required packages are installed and your python environment is activated.

## Usage

- launch *CARLA Simulator*

```shell
cd <CARLA Project>
./CarlaUE4.sh
```

### Setup Camera

- set camera by running 

  ```shell
  python start_recording.py --config_name=test.json --auto_save=False --flag_show_windows=True --recording_num_scale=0
  ```

  or

  ```shell
  ./select_viewpoint.sh
  ```

  > use the short cut key to move camera and fix its viewpoint.

### Recording

- modify the configure files as you want, in our example, we use test.json which is generated by "Setup Camera"

  ```json
  {
      "cameras": {
          "Easy_Camera_Cross1": {
              "fov": 90.0,
              "height": 1080,
              "max_record_frame": 10,
              "pitch": -42.999786376953125,
              "roll": 1.0506457329029217e-05,
              "width": 1920,
              "x": -79.3550796508789,
              "y": -0.8948922753334045,
              "yaw": 42.000396728515625,
              "z": 32.788326263427734
          },
          "Hard_Town3_Test_00": {
              "fov": 90.0,
              "height": 1080,
              "max_record_frame": 10000,
              "pitch": 0.0,
              "roll": 0.0,
              "width": 1920,
              "x": -78.0,
              "y": 8.300000190734863,
              "yaw": 0.0,
              "z": 39.0
          }
      },
      "host": "127.0.0.1",
      "mode": "parallel", 
      "port": 2000,
      "save_root": "/home/ssj/Data/github/AwesomeMOTDataset/Dataset/Temp",
      "vehicle_num": [
          30,
          45,
          50
      ],
      "weathers": [
          "Clear",
          "Cloudy",
          "Rain"
      ]
  }
  ```

- Run a script

  ```shell
  python start_recording.py --config_name=test.json --auto_save=True --flag_show_windows=True --recording_num_scale=0.5
  ```

  or

  ```shell
  ./start_recording.sh
  ```

  

### Short Cut Key

| Key    | Action                              |
| ------ | ----------------------------------- |
| Esc    | Quit                                |
| Insert | Insert a new camera                 |
| Enter  | Save all camera parameters          |
| Tab    | Switch the Cameras                  |
| 1      | Start Image Processing              |
| 2      | Show 3D Bounding Boxes in the Image |
| 3      | Show Rectangle in the Image         |
| 4      | Show Vehicle Labels                 |
| w      | Move Forward                        |
| s      | Move Backward                       |
| a      | Move Left                           |
| d      | Move Right                          |
| q      | Move Up                             |
| e      | Move Down                           |
| i      | Pitch Up                            |
| k      | Pitch Down                          |
| j      | Roll Left                           |
| l      | Roll Right                          |
| u      | Yaw Left                            |
| p      | Yaw Right                           |
| Home   | Update the Camera Level             |

## Citation

Paper will be released soon :-).

## Acknowledge

This work is based on the [CARLA](https://github.com/carla-simulator/carla) . It is also inspired by [SSD](https://github.com/amdegroot/ssd.pytorch) and [DAN](https://www.researchgate.net/publication/334508412_Deep_Affinity_Network_for_Multiple_Object_Tracking).

## License

CARLA specific code is distributed under MIT License.

CARLA specific assets are distributed under CC-BY License.

Note that UE4 itself follows its own license terms.



