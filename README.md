
  git clone http://github.com/tiiuae/nv-build-scripts
  mv nv-build-scripts workdir && cd workdir
  ./sync_sources.sh -t ....
  pushd kernel
  git clone --depth 1 ....
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
  cp .config arch/arm64/configs/defconfig 
  popd
  popd
  # check settings 
  ./nvbuild.sh
  
