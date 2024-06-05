# Jupyter Notebook
First step is to build out your container for the notebook:
- `docker build -t hw1-jupyter -f docker/Dockerfile .`

The next step is to run the container, mount your pysical drive, then navigate in your browser to `localhost:8888` to access the contents:
docker run -p 8888:8888 -v $(pwd):/workspace:Z hw1-jupyter

- If you installed the Nvidia Container Toolkit and wish to use GPU: (see https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/cdi-support.html)

- `docker run --hooks-dir=/usr/share/containers/oci/hooks.d --gpus all -p 8888:8888 -v $(pwd):/workspace:z hw1-jupyter`

NOTE: If you created this container and have since updated your drivers, you'll need to regenerate the CDI specification with `sudo nvidia-ctk cdi generate --output=/etc/cdi/nvidia.yaml`

docker system prune -af
