# images can be found on https://hub.docker.com/
FROM pytorch/pytorch:2.3.0-cuda12.1-cudnn8-runtime

# Install packages here
RUN apt-get update -y && \
    apt-get install -y git build-essential libssl-dev && \
    # Upgrade pip to the latest version
    pip install --no-cache-dir --upgrade pip && \
    # Install Jupyter and whatever other Python packages using pip
    pip install --no-cache-dir jupyter pandas numpy matplotlib scikit-learn && \
    # Clean up to reduce image size
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set up the working directory, this is where you get 'dropped into' the container
WORKDIR /workspace

# Expose the port for Jupyter Notebook
EXPOSE 8888

# Start Jupyter Notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--allow-root", "--NotebookApp.token=''", "--NotebookApp.password=''"]
