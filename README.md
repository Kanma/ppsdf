# ppSDF

![reconstructions](https://github.com/maricante/ppSDF/assets/13221985/af6102b2-06bf-4d0c-8a71-5c6b23784950)

Code examples for [*Online learning of Continuous Signed Distance Fields Using Piecewise Polynomials*](https://sites.google.com/view/pp-sdf/).

This repository started as a fork of [the RDF codebase](https://gitlab.idiap.ch/rli/RDF).
## Dependencies

Tested with *Python 3.10.12* on *Ubuntu 22.04* and *macOS 14.4.1*.

Python dependencies are listed in `requirements.txt`. *Open3D* additionally requires a working C++ compiler.

*(Optional)* For GPU acceleration, a compatible version of CUDA is required (tested with CUDA 11.5).

## Conda setup

Setup a conda new environment:

    conda create --name ppSDF python=3.10.12

Activate the environment:

    conda activate ppSDF

Install the required packages:

    pip install -r requirements.txt

## Downloading the YCB dataset

The desired objects from the [YCB dataset (*Calli et al.*)](http://ycb-benchmarks.s3-website-us-east-1.amazonaws.com/) can be downloaded by running

    python ycb_downloader.py

Objects can be selected by commenting/uncommenting elements in the `objects_to_download` list inside the script.

## Running the example script

To run the example script with the desired arguments:

- `n_seg` - number of segments per input dimension
- `qd`, `qn`, `qt` - cost coefficients for incremental learning
- `sigma` - measurement noise
- `batch_size` - batch size for the incremental updates
- `device` - device to run on (e.g., `cuda` or `cpu`)
- `save` - if `True`, saves the approximated SDF
- `object` - which object to load
- `n_data` - number of training sample points
- `cut_x`, `cut_y`, `cut_z` - select axis to cut for visualization

For example, to approximate the '035_power_drill' object with 5 segments per input dimension and 1000 training samples:

    python reconstruct.py --object=035_power_drill --n_seg=5 --n_data=1000

To run with default arguments:

    python reconstruct.py

## License

Maintained by Ante MARIĆ and licensed under the GPL-3.0 License.

Copyright (c) 2024 Idiap Research Institute <contact@idiap.ch>
