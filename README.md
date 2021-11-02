# openairinterface_lmssdr
Decode SA air msg with  openairinterface and lmssdr 

Openairinterface_lmssdr is a free and open-source project for SA cell air msg check.

Openairinterface_lmssdr is released under the AGPLv3 license and uses software from the openairinterface project. 

1 Add lmssdr support
  sudo apt-get install limesuite liblimesuite-dev limesuite-udev
  in openairinterface develop branch ./cmake_targets/build_oai  -w LMSSDR --gNB --nrUE
  If you get LMS_EnableCache() error in compilations,  you can comment LMS_EnableCache(). For detail infomation,pls can check this 
      https://open-cells.com/index.php/2018/05/04/limesdr-new-set-of-tests/
  
2 Decode SA air msg
  sudo ./nr-uesoftmodem  --ue-rxgain 85 --ue-txgain 0 --band 41 -C 2524950000  -r 51 --numerology 1 -s 186  --ue-nb-ant-tx 1 --ue-nb-ant-rx 1  \
       --rf-config-file targets/ARCH/LMSSDR/LimeSDR_above_1p8GHz_1v4.ini   --sa
  
   2524950000 is CMCC n41 carrier ssb frequency. 34089600 and 3509760000 is  CUCC and CTCC n78 carrier ssb frequency.
   r51 with 30.72MSPS and r106 with 61.44MSPS.
   
 On ubuntu 20.04 with intel I5 4core CPU receive MIB ok. Sib1 is still on development. ue-rxgain can change from 40 to 115 .
