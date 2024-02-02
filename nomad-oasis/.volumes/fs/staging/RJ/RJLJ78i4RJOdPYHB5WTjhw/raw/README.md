# STM example reader
In this example three example experimental files (STM_Example_file_1.sxm, STS_Example_file_1.dat and 
STS_Example_file_2.dat) are provided.

Other two important files are [config_file_for_dat.json](config_file_for_dat.json) and 
[config_file_for_sxm.json](config_file_for_sxm.json). These two files are intended to connect 
between raw data path to concept from NXiv_sweep2.nxdl.xml. 
To have a look raw data path used inside reader one can use the following code that will generate
corresponding output file:

```
from pynxtools.dataconverter.readers.stm import get_stm_raw_file_info
from pynxtools.dataconverter.readers.stm import get_sts_raw_file_info

# for stm (.sxm) file
get_stm_raw_file_info('STM_Example_file_1.sxm')

# for sts (.dat) file
get_sts_raw_file_info('STS_Example_file_1.dat')

```
To connect further the experiment data path to the concept in
[config_file_for_dat.json](config_file_for_dat.json)
and [config_file_for_sxm.json](config_file_for_sxm.json) one can take help of raw data explanation 
obtained from code above.

In this example folder other two important ELN files 1. [Nanonis_Eln.yaml](Nanonis_Eln.yaml)
and 2. [STM.scheme.archive.yaml](STM.scheme.archive.yaml). The ELN-1 needed to run the reader from
console or jupyter-notebook and ELN-2 to run the reader from Nomad software (Note that NOMAD 
software will generate an ELN named eln_data.yaml analogous to ELN-1 to launch reader.).

## Run STM reader 
STM reader can be run from jupyter notebook or console with the following code snippet

For stm experiment use the following code:
```
!dataconverter \
--reader stm \
--nxdl NXiv_sweep2 \
--input-file <PATH TO>/STM_Example_file_1.sxm \
--input-file <PATH TO>/config_file_for_sxm.json \
--input-file <PATH TO>/Nanonis_Eln.yaml \
--output stm_output.nxs
```

For sts experiment use the following code:
```
!dataconverter \
--reader stm \
--nxdl NXiv_sweep2 \
--input-file <PATH TO>/STS_Example_file_1.dat \
--input-file <PATH TO>/config_file_for_dat.json \
--input-file <PATH TO>/Nanonis_Eln.yaml \
--output sts_output.nxs
```

For launching stm reader from jupyter notebook one can use 
[NotebookForSTM_STS_CONVERTER.ipynb](NotebookForSTM_STS_CONVERTER.ipynb) in this derectory.

## Supported Vendors and Version
Coming soon!

## OOPS
Still have issue write an issue in [pynxtools](https://github.com/FAIRmat-NFDI/pynxtools) or reach 
out to responsible person [@Rubel Mozumder](mozumder@physik.hu-berlin.de).
