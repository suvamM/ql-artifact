# Getting Started Guide

## Requirements
- [Git](https://git-scm.com/download/)
- [VirtualBox](https://www.virtualbox.org/): While any recent version should suffice, we built and tested our artifact using version 6.1.12.
## Setting up
- Clone this repository (`git clone https://github.com/suvamM/ql-artifact.git`) from a terminal. This will download the VirtualBox image file (`.vdi`). 
- In VirtualBox, select `File -> Import Appliance`, and then select the `vdi` image file. After the import is completed, you should now see `QL` as one of the listed VMs in your VirtualBox app.
- Run the `QL` virtual machine. The username is `ql` and the password is `qltest`.
- In the home folder (`/home/ql`), there is a `oopsla/psharp-ql` directory which contains all the sources (P# tester with the implementation for `QL`, and the non-proprietary benchmarks), along with scripts for running the experiments.
- Open a terminal (from Favorites or `Ctrl + Alt + T`), and run `powershell`. 
- Build the P#-tester: `./build.ps1` in `oopsla/psharp-ql`. 
- Goto the Benchmarks directory: `cd Benchmarks`
- Build the benchmarks, along with the program to drive the experiments (`EvaluationDriver'): `./build-benchmarks.ps1`

Everything is now setup!

## Test
To quickly test the setup, run the command `./run-benchmarks.ps1 -mode "test" -numEpochs 1` from the Benchmarks folder. This will run the `Raft-v1` benchmark, and the configuration of the test (number of iterations, max-steps, etc) are present in the JSON configuration file under `Benchmarks/Test`. By default, the P#-tester will be invoked 100 times to obtain the B-100 metric (the `NumEpochs` value is set to 100 in the JSON). The `-numEpochs 1` overrides this value, to report B-1 instead, for quick evaluation. Finally, a csv file summarizing the results (similar to the `Raft-v1` row in Table 2 of the paper) is created under `Benchmarks`. 
