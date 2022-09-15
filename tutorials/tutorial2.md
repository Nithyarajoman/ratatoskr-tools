# Tutorial 2: ratatoskr GUI client

In this tutorial, you will know how to use the ratatoskr GUI client, which let you to see the router heat (traffic business) of the NoC.

## Prerequisite

Before the tutorial, it is required that to compile and retrieve the simulator (./sim) from the ratatoskr simulator repository. During the simulation the sim executable and the network plotting script should be provided with the same port numbers(as illustrated in the below example). This will enable multiple GUI simulations to be carried out simulatneously.

## Step 1 Network Configuration
Create the config.ini file and generate the config.xml and network.xml files.


```python
import ratatoskr_tools.networkconfig as rtcfg

rtcfg.create_config_ini("./tutorials/example/config.ini")
config = rtcfg.create_configuration(".tutorials/example/config.ini", "./tutorials/example/config.xml", "./tutorials/example/network.xml")
```

## Step 2 Dynamic Network Plotting

Use the provided API to run the ratatoskr GUI client. The function "plot_dynamic()" accepts the network.xml, config.xml, port address is randomly selected as 6000 (by default it would be 5555).


```python
import ratatoskr_tools.networkplot as rtnplt

rtnplt.plot_dynamic("./tutorials/example/network.xml", "./tutorials/example/config.ini","localhost","6000")
```

## Step 3 Run the simulation.

Open another terminal to run the simulation, where this simulator is compiled. The same port address provided for GUI client is given here.

> $ ./sim --configPath=./example/config.xml --networkPath=./example/network.xml --outputDir=./example --GUI_Port_address=6000

The ratatoskr GUI client windows will be opened.

## Step 4 Run multiple simulations.

Now multiple simulations with GUI can be done. For this create a different folder "example2" and perform the below for creating the input files for the simulator. When the GUI plot function is called it should be assigned to a different port address than the one used above which was 6000. An the same new port address should be given for simulation using the sim executable. 

'''python
import ratatoskr_tools.networkconfig as rtcfg
rtcfg.create_config_ini("./tutorials/example2/config.ini")
config = rtcfg.create_configuration("./tutorials/example2/config.ini", "./tutorials/example2/config.xml", "./tutorials/example2/network.xml")

import ratatoskr_tools.networkplot as rtnplt
rtnplt.plot_dynamic("./tutorials/example2/network.xml", "./tutorials/example2/config.ini","localhost","7000")
'''

The execution of the sim file to be carried out in a different terminal
> $ ./sim --configPath=./tutorials/example2/config.xml --networkPath=./tutorials/example2/network.xml --outputDir=./tutorials/example2 --GUI_Port_address=7000
