# Reference
https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action

# Hello world docker action

This action prints "Hello World" or "Hello" + the name of a person to greet to the log.

## Inputs

## `who-to-greet`

**Required** The name of the person to greet. Default `"World"`.

## Outputs

## `time`

The time we greeted you.

## Workflow
.github/workflows/main.yml
  - Whenever "push" happens, run a job, which runs the action "action.yml" with input "who-to-greet: 'Taro Boy'".  Then print the output from the action, which is the current time
action.yml
  - Runs the docker specified in Dockerfile.  Grab the output from docker
Dockerfile
  - Specifies the base image, copy a script "entrypoint.sh" and run the script
entrypoint.sh
  - Print out the greeting message and returns the current time

