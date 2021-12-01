# Problems and solutions

## Matplotlib and keras together cause problems. [SOLVED]
### Description
Keras methods crash when matplotlib methods were called. Matplotlib methods crash when Keras methods were called.

### Steps taken
#### Reinstalling virtual environment
Env Tensorflow:
<ol>
    <li>Python version 3.7.11</li>
    <li>conda install -c conda-forge tensorflow => v1.14</li>
    <li>Installed jupyted notebook</li>
    <li>Executed jupyter notebook => errors Tensorflow version outdated</li>
    <li>conda update tensorflow -c anaconda => v2.1.0 (niet 2.6 zoals op site)</li>
    <li>conda update tensorflow -no-priority-channel => v2.1.0</li>
    <li>...</li>
</ol>
Env Tensorflow_Python38:
<ol>
    <li>Python version 3.8</li>
    <li>conda install tensorflow -c anaconda => v2.3.0 (niet 2.6 zoals op site)</li>
    <li>...</li>
</ol>
<strong>Env Tensorflow_Python39:</strong>
<ol>
    <li>Python version 3.9</li>
    <li>conda install -c anaconda tensorflow => v2.6.0</li>
    <li>Installed jupyted notebook</li>
    <li>conda install -c conda-forge matplotlib (worked but 2 times: failed with initial frozen solve. Retrying with flexible solve.)</li>
    <li>Executed j notebook ClothingAI => same error</li>
    <li>conda uninstall matplotlib</li>
    <li>base(root): conda update -n base conda</li>
    <li>base(root): conda update --all</li>
    <li>conda install -c conda-forge matplotlib</li>
    <li>Executed j notebook ClothingAI => same error</li>
    <li>conda uninstall matplotlib => (ERROR conda.core.link:_execute(699): An error occurred while installing package 'defaults::openssl-1.1.1l-h2bbff1b_0'. Rolling back transaction: done)</li>
    <li><span style="background-color: #436A5B">pip uninstall tensorflow<span></li>
    <li><span style="background-color: #436A5B">pip install tensorflow<span></li>
    <li><strong>**WORKS!!!!!!!!!!!**:</strong> 
    https://stackoverflow.com/questions/53014306/error-15-initializing-libiomp5-dylib-but-found-libiomp5-dylib-already-initial</li>
</ol>
Env Tensorflow_Python39_mpl-base
<ol>
    <li>Python version 3.9</li>
    <li>conda install -c conda-forge matplotlib-base (No solving problems)</li>
    <li>conda install -c anaconda tensorflow => 2 solving problems: DIDN'T EXECUTE</li>
    <li>conda install -c conda tensorflow => 2 solving problems but only 1 downgrade by channel</li>
    <li><strong>I ran the code in terminal: See error output 1</strong></li>
    <li>...</li>
</ol>

#### Error output

```
2021-10-27 10:45:25.678709: I tensorflow/core/platform/cpu_feature_guard.cc:142] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN) to use the following CPU instructions in performance-critical operations:  AVX2
To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.
OMP: Error #15: Initializing libiomp5, but found libiomp5md.dll already initialized.
OMP: Hint This means that multiple copies of the OpenMP runtime have been linked into the program. That is dangerous, since it can degrade performance or cause incorrect results. The best thing to do is to ensure that only a single OpenMP runtime is linked into the process, e.g. by avoiding static linking of the OpenMP runtime in any library. As an unsafe, unsupported, undocumented workaround you can set the environment variable KMP_DUPLICATE_LIB_OK=TRUE to allow the program to continue to execute, but that may cause crashes or silently produce incorrect results. For more information, please see http://openmp.llvm.org/
```

