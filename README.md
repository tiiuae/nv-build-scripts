
  git clone http://github.com/tiiuae/nv-build-scripts
  
  mv nv-build-scripts workdir && cd workdir
  
  ./source_sync.sh -k rel-36_eng_2024-04-04
  \# another possible tag is l4t-l4t-r36.3_eng_2024-04-24
  
  pushd kernel
  
  git clone --depth 1 https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git --branch v6.8.7 
  
  mv linux kernel-687
  
  pushd kernel-687
  
  make defconfig
  
  scripts/config --file .config --enable ARM64_PMEM
  
  scripts/config --file .config --enable PCIE_TEGRA194
  
  scripts/config --file .config --enable PCIE_TEGRA194_HOST
  
  scripts/config --file .config --enable BLK_DEV_NVME
  
  scripts/config --file .config --enable NVME_CORE
  
  scripts/config --file .config --enable FB_SIMPLE
  
  scripts/config --file .config --enable RTW88

  scripts/config --file .config --enable RTW88_8822CE
  
  cp .config arch/arm64/configs/defconfig 
  
  popd
  
  popd
  
  \# check settings 
  
  ./nvbuild.sh
  
