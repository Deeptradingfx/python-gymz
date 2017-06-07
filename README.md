# gymz
[![Python2.7](https://img.shields.io/badge/python-2.7-blue.svg)](https://www.python.org/)
[![License](http://img.shields.io/:license-MIT-green.svg)](https://opensource.org/licenses/MIT)

gymz provides a light-weight wrapper around the [OpenAI Gym](https://gym.openai.com/) to allow interaction with reinforcement learning environments via [ZeroMQ](http://zeromq.org/) sockets.

The wrapper consists of four different threads that coordinate

1. performing steps in an environment
2. receiving actions via a ZeroMQ SUB socket
3. publishing observations via a ZeroMQ PUB socket
4. publishing rewards via a ZeroMQ PUB socket

It was initially designed to be used in combination with [MUSIC](https://github.com/incf-music) enabling online interaction between reinforcement learning environments from the OpenAI Gym and neuronal network models in simulators like [NEST](http://nest-simulator.org/) or [NEURON](http://www.neuron.yale.edu/neuron/).

## Installing gymz
gymz is available via pip:

```bash
pip install gymz
```

## Quickstart
An example client is provided (`examples/random_zmq_client.py`) that connects to a running instance of the wrapper, sends random actions and prints observations and rewards received from the environment to the screen. From a terminal start the wrapper with the default configuration file:

```bash
python controller.py gym DefaultConfig.json
```

and the `MountainCar-v0` environment should be rendered on the screen. Afterwards start the client with:

```bash
python random_zmq_client.py
```

The client should now continously print commands, observations and rewards to the terminal. If it does not, please report the issue.
