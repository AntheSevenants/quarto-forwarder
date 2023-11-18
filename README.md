# quarto-forwarder
Forward 'quarto preview' request to a Docker container with Quarto installed

## The situation

This repository proposes a solution for the following, admittedly very niche situation:

- you use VS Code
- you use the official [Quarto extension](https://marketplace.visualstudio.com/items?itemName=quarto.quarto)
- you'd like to have Quarto and R (or Python, for what it's worth) installed inside a **Docker container**

### The problem

The problem with this specific situation is that the Quarto VS Code extension expects Quarto to be installed locally.

### The solution

I designed a Quarto 'wrapper' which intercepts the call to `quarto preview` and forwards it to the Docker container where Quarto is running.

### How to use

1. Download the `quarto` script from this repository
2. Change `DOCKER_CONTAINER_NAME` to the name of the container where Quarto is installed  
    Change `QMD_DOCKER_PATH` to the path of your Quarto document **inside the container**
3. Make sure to forward port 8788 inside your `docker-compose` file (or however you're running your Docker container)
4. You can now press CTRL ^ SHIFT ^ K and have your `quarto preview` request forwarded to your Docker container.

May your articles be accepted :-).