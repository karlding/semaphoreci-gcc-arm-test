# Semaphore CI Job setup

## No Caching

```bash
# gcc-arm-embedded
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv B4D03348F75E3362B1E1C2A1D1FAA6ECF64D33B0
echo "deb http://ppa.launchpad.net/team-gcc-arm-embedded/ppa/ubuntu trusty main" | sudo tee /etc/apt/sources.list.d/team-gcc-arm-embedded.list
install-package --update-new gcc-arm-embedded
# gcc 6
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 60C317803A41BA51845E371A1E9377A2BA9EF27F
echo "deb http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu trusty main" | sudo tee /etc/apt/sources.list.d/ubuntu-toolchain-r-test.list
install-package --update-new gcc-6
install-package --update-new g++-6
# python3 pip
install-package --update-new python3-pip
# build make
wget http://ftp.gnu.org/gnu/make/make-4.1.tar.gz && tar xvzf make-4.1.tar.gz && rm make-4.1.tar.gz
cd make-4.1
./configure && make && sudo make install
cd - && rm -rf make-4.1
# update $PATH
hash -r
```
