## Summary
It implements a workflow to pull the NRF connect SDK container.  Then build code for Nordic 52840 in it, and deploys the output hex file.

## Workflow
.github/workflows/main.yml
  - Whenever "push" happens, run a job
  - job
    - Runs on the latest Ubuntu
    - Pulls the NRF connect SDK container so that all the steps below will run in the container
    - Steps
      - Go to the project directory
        - The NRF connect SDK container provides the project directory where you can build your projects, so go there
      - Checkout source code
        - Checkout the source code in this repository into the project directory in the container so we can build it.  The source code is the copy of the sample project that comes when you install the NRF connect SDK.  The sample project is located at C:\ncs\v2.2.0\nrf\samples\bluetooth\central_and_peripheral_hr.
      - Build code
        - Build the source code using the specified board and build directory.  
      - Prepare artifact
        - The build output is a hex file which you can upload to program the microcontroller.  It will place the hex file in a dedicated artifact folder.
      - Upload artifact
        - Upload the hex file as an artifact.  The artifact is available for download in the Artifacts section of the run.  Example: https://github.com/ktotsuka/nrf-ci/actions/runs/3962353890

## Design consideration
Using a docker is the simplest way to build code for Nordic SDK.  Nordic Semiconductor provides a docker container for it at https://github.com/NordicPlayground/nrf-docker.  

Using Github actions is the simplest way to set up a simple CI/CD because you can do everything there.  There is no need to hook up with other websites like Jenkins.  