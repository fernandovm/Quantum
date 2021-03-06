# Qiskit Sample #

This sample shows that one can run the quantum operations of a Q# application on the IBMQuantumExperience by only changing the driver.

## 0. Requirements ##

- **Python IBMQuantumExperience**
  This sample uses the IBMQuantumExperience python3 package to communicate run the qasm on either the IBM Q machine of the Qasm emulator. 
  IBMQuantumExperience can be installed by running 'pip3 install IBMQuantumExperience'
  Because IBMQuantumExperience is known to have some issues on Windows, the linux subsystem might be needed to run the example.
  In that case the python3 of the linux subsystem needs to be first in the path in order to execute.
- **API Key**
  This sample uses an api key for authorisation to the quantum experience API.
  One needs to have an account and create an api key at: https://quantumexperience.ng.bluemix.net/qx/account/advanced
  This api key can then be set in Driver.cs.

## 1. Expected outcome ##

If done correctly, the driver will generate QASM for the Hadamard gate:
```
Hadamard on IBMQx4

QASM file
include "qelib1.inc";
qreg q[5];
creg c[5];
h q[0];
measure q[0] -> c[0];
```
It will then start the interface to send the QASM to the quantum experience
```
Usage: python3 QiskitInterface.py <Key> <Backend>
['QiskitInterface.py', '610320e...097f48815', 'ibmqx4']
Qiskit API Interface
QASM FILE READ
include "qelib1.inc";
qreg q[5];
creg c[5];
h q[0];
measure q[0] -> c[0];

SENDING TO IBM Quantum Experience
 IBMQ AT IBM Quantum Experience:
 JobID: 899ae398dc2a4546a350edfb9ef78b0d
 Expected time (minutes) in Queue left: 3.6
 SIMULATOR AT IBM:
```
If the api indicates that it will take longer than a minute to execute, a fallback to the ibm simulator will be used:
```
DONE
{'status': 'DONE', 'idExecution': 'b68aaa1be43e90b554b9c5aca979d013', 'result': {'measure': {'labels': ['00001'], 'values': [1], 'qubits': [0]}, 'extraInfo': {'seed': 2939514402}}, 'idCode': '4f24e8dd5ca06585b9a457ede0e5cb9c'}

Processed
Result=00001
Result of Hadamard is One
Press Enter to continue...
```
Showing that it can be done.