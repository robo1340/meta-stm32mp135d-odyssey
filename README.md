This README file contains information on the contents of the meta-iris layer.

Please see the corresponding sections below for details.

Dependencies
============

  URI: <first dependency>
  branch: <branch name>

  URI: <second dependency>
  branch: <branch name>

  .
  .
  .

Building Image for STM32mp135d-odyssey
=======

place this layer in your build system and add it to bblayers.conf
bitbake-layers add-layer meta-stm32mp135d-odyssey

now use the devtool to check out the source for the following recipes
devtool modify tf-a-stm32mp
devtool modify u-boot-stm32mp
devtool modify linux-stm32mp
devtool modify optee-os-stm32mp

remove everything in each workspace that gets created
i.e.
cd ~/stm32mp1/build/workspace/sources/tf-a-stm32mp
rm -rf ./*

clone in my own custom repos into each respective directory you cleared out (I know, this is an abuse of the yocto build system)
git clone https://github.com/robo1340/optee-os-stm32mp.git
git clone https://github.com/robo1340/linux-stm32mp.git
git clone https://github.com/robo1340/tf-a-stm32mp.git
git clone https://github.com/robo1340/u-boot-stm32mp.git

now build the image
bitbake st-image-core
