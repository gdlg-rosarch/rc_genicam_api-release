# Script generated with Bloom
pkgdesc="ROS - GenICam/GigE Vision Convenience Layer. This package combines the Roboception convenience layer for images with the GenICam reference implementation and a GigE Vision transport layer. It is a self contained package that permits configuration and image streaming of GenICam / GigE Vision 2.0 compatible cameras like the Roboception rc_visard. This package also provides some tools that can be called from the command line for discovering cameras, changing their configuration and streaming images. Although the tools are meant to be useful when working in a shell or in a script, their main purpose is to serve as example on how to use the API for reading and setting parameters, streaming and synchronizing images. See LICENSE.md for licensing terms of the different parts."


pkgname='ros-lunar-rc-genicam-api'
pkgver='1.3.6_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('cmake'
)

depends=('ros-lunar-catkin'
)

conflicts=()
replaces=()

_dir=rc_genicam_api
source=()
md5sums=()

prepare() {
    cp -R $startdir/rc_genicam_api $srcdir/rc_genicam_api
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

