# LIO-SAM Orchard Reconstruction Configuration

This repository provides the configuration files and execution instructions used to run the original **[LIO-SAM](https://github.com/TixiaoShan/LIO-SAM/tree/master)** algorithm for 3D reconstruction of fruit-tree orchards.

The repository is intended as a reproducibility package for the manuscript:

> **Benchmarking cost-effective LiDAR-SLAM systems for 3D fruit orchard reconstruction and geometric characterisation**  
> **Marc Felip-Pomés, Jordi Gené-Mola, Jordi Llorens-Calveras,                        Ricardo Sanz-Cortiella, Alexandre Escolà, Jaume Lordan, José M. Plata, Eduard Gregorio**  
> Submitted to *Biosystems Engineering*.

## Purpose of this repository

The core LIO-SAM algorithm was **not modified** in this study. The original ROS1 implementation of LIO-SAM was used as released by Shan et al. The files provided here document the dataset configuration used in the orchard reconstruction experiments.

The purpose of this repository is to help reproduce the data processing workflow used in the paper

## Relationship with the original LIO-SAM repository

Users should first install the original LIO-SAM ROS1 package:

```bash
cd ~/catkin_ws/src
git clone https://github.com/TixiaoShan/LIO-SAM.git
cd ..
catkin_make
```

Then copy the files from this repository into the corresponding LIO-SAM folders:

```bash
# From the root folder of this repository
cp config/params_ouster.yaml ~/catkin_ws/src/LIO-SAM/config/
cp config/params_livox.yaml  ~/catkin_ws/src/LIO-SAM/config/
cp launch/run_orchard.launch ~/catkin_ws/src/LIO-SAM/launch/
```

Alternatively, the content of `params_ouster.yaml` or `params_livox.yaml` can be copied into `LIO-SAM/config/params.yaml`, and the original LIO-SAM launch file can be used without modification.

## Repository structure

```text
lio-sam-orchard-reconstruction/
├── README.md
├── LICENSE
├── config/
│   ├── params_ouster.yaml
│   └── params_livox.yaml
├── launch/
│   └── run_orchard.launch
└── docs/
    └── dataset_description.md
```

## Configuration files

Two configuration files are provided:

| File | LiDAR sensor | Purpose |
|---|---|---|
| `config/params_ouster.yaml` | Ouster OS0-128 | Orchard reconstruction using the Ouster LiDAR setup |
| `config/params_livox.yaml` | Livox Mid-360 | Orchard reconstruction using the Livox LiDAR setup |


## Running the experiments

After installing LIO-SAM and copying the files as described above, run the Ouster configuration with:

```bash
roslaunch lio_sam run_orchard.launch config_file:=params_ouster.yaml
rosbag play /path/to/ouster_dataset.bag
```

Run the Livox Mid-360 configuration with:

```bash
roslaunch lio_sam run_orchard.launch config_file:=params_livox.yaml
rosbag play /path/to/livox_dataset.bag
```

If you prefer to keep the original LIO-SAM `run.launch`, replace the original `config/params.yaml` file with the corresponding configuration file from this repository before launching LIO-SAM:

```bash
cp config/params_ouster.yaml ~/catkin_ws/src/LIO-SAM/config/params.yaml
roslaunch lio_sam run.launch
```

## Dataset availability

The rosbag datasets used to generate the results reported in the paper are available at:

> **[Dataset URL](https://irtacat-my.sharepoint.com/:f:/g/personal/marc_felip_irta_cat/IgDFIjUl8ma1TJKj7rw3kUrRASQ7X8_j5jnBlEXROTZm8Qc?e=YG3FgY)**

The dataset description is provided in [`docs/dataset_description.md`](docs/dataset_description.md).

## Notes for reproducibility

- The configuration files correspond to the experimental setup used in the manuscript.
- The output directory for saved point clouds is set through `savePCDDirectory` and should be adapted to the user's computer before running the package.
- The number of CPU cores is set to `16`, matching the processing workstation used in the experiments. This can be reduced if required.
- Loop closure was disabled in the published configuration with `loopClosureEnableFlag: false`.
- The original LIO-SAM package should be cited when using this configuration.

## Acknowledgements

This work has been developed within the framework of project TED2021-131871B-I00
([DIGIFRUIT project](https://www.grap.udl.cat/en/recerca/projectes-de-recerca/digifruit/)), funded by the
Spanish Ministry of Science, Innovation and Universities
(MICIU)/AEI/10.13039/501100011033 and by the European Union
NextGenerationEU/PRTR.

This research was also partly funded by the Department of Research and
Universities of the Generalitat de Catalunya (grant 2017 SGR 646); by the
Spanish Ministry of Science and Innovation/AEI/10.13039/501100011033/ERDF
through projects PID2021-126648OB-I00 (PAgPROTECT project) and
PID2024-156495OR-C31 (YIELD4CAST project); and by the Agrotecnio-IRTA Joint
Projects Call 2025 (PhotonFruit project).


<p align="center">
  <img
    src="docs/funding/gene.png"
    alt="Generalitat de Catalunya"
    height="75"
  >
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img
    src="docs/funding/udl.png"
    alt="Universitat de Lleida"
    height="90"
  >
</p>

<p align="center">
  <img
    src="docs/funding/agrotecnio.png"
    alt="Agrotecnio"
    height="85"
  >
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img
    src="docs/funding/IRTA.png"
    alt="IRTA"
    height="75"
  >
</p>

<p align="center">
  <img
    src="docs\funding\TED_MICIU+NextG+PRTR+AEI.jpg"
    alt="DIGIFRUIT project funding: MICIU, AEI, European Union NextGenerationEU and PRTR"
    width="50%"
  >
</p>

<p align="center">
  <img
    src="docs\funding\PAGPROTECT_MICIU+Cofinanciado+AEI.jpg"
    alt="PAgPROTECT project funding: MICIU, AEI and European Union"
    width="50%"
  >
</p>


##  Notice

This repository provides configuration files, documentation, and launch instructions for reproducing LIO-SAM-based orchard reconstruction experiments.

The core LIO-SAM algorithm was not modified and is not redistributed here. Users should obtain the original LIO-SAM implementation from:

https://github.com/TixiaoShan/LIO-SAM

Some configuration and launch-file structure in this repository is adapted from the original LIO-SAM repository, which is distributed under the BSD 3-Clause License.

## License

This repository is released under the BSD 3-Clause License. See [`LICENSE`](LICENSE) for details.
