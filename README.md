# YACS
A centralized scheduling tool which simulates the scheduling of tasks in a distributed setting. This project was done for the UE18CS322 course on Big Data, at PES University. 

## Table Of Contents:
* [Directory Structure](#directory-structure)
* [Initial Setup](#initial-setup)
* [Execution](#execution)

## Directory Structure:
```
.
|-- data
|   |-- LL
|   |   |-- . 
|   |-- RANDOM
|   |   |-- . 
|   |-- RR
|   |   |-- . 
|   |-- config.json
|-- src
|   |-- analysis.py
|   |-- master.py
|   |-- requests_eval.py
|   |-- requests.py
|   |-- worker.py
```
### Description:
* ```data``` contains the log files along with the config file required for the master. Log files are written as ```.csv``` files into respective folders based on the scheduling algorithm used.
* ```src``` contains the source code for the master, workers, job creation and analysis.

## Initial Setup:
### Get source code:
Clone the repository by executing the following commands:
```
git clone https://github.com/morpheu513/YACS.git
cd YACS

```

### Requirements:
* Python 3.6.x

<br>

To install dependencies type in the following command:
```
pip install -r requirements.txt
```


## Execution:
Follow the given steps to execute the source code.
### Start master:
On a new terminal run the ```master.py``` file. This file takes in positional arguments, first one is the path to the ```config.json``` file and the second one is the type of scheduling algorithm to be used. For example if we want to use Round-robin scheduling, we would type:
```
python3 master.py '<path-to-config.json-file>' 'RR'
```
#### Supported Scheduling Algorithms:
* RR - Round Robin
* LL - Least Loaded
* R - Random

### Start workers:
Depending on the number of workers provided in the ```config.json``` file, we should start those many workers.
<br>

The ```worker.py``` file takes in 2 positional arguments which are as follows, the first one is the port number on which the worker listen to updates from the master and the second one is the worker id.
<br>

Both these values should match with the values provided in the ```config.json``` file. For example if we want to start the worker with id=2 and port number 5000, we would type in the following command:
```
python3 worker.py 5000 1
```
### Generate requests:
Requests or Jobs can be generated using both the ```requests.py``` and ```requests_eval.py``` files. If your using the ```requests.py``` file you should pass a single argument while executing it, which defines the number of jobs/requests generated.
<br>

If your using the ```requests_eval.py``` file you have to provide specific information of the request, like the number of map tasks, duration of job,etc.

### Perform analysis:
To return results like the mean job execution time, mean task execution time, etc the ```analysis.py``` file should be run. This file takes in one argument which is, the number of workers present in the current configuration.
<br>

For example if we have 3 workers in our configuration then the command would be:
```
python3 analysis.py 3
```
**Note:** Ensure that all log files(for all scheduling algorithms) are generated correctly before running the ```analysis.py``` file.
