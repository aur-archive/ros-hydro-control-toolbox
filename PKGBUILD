# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - The control toolbox contains modules that are useful across all controllers."
url='http://ros.org/wiki/control_toolbox'

pkgname='ros-hydro-control-toolbox'
pkgver='1.10.4'
_pkgver_patch=2
arch=('any')
pkgrel=2
license=('BSD')

ros_makedepends=(ros-hydro-message-generation
  ros-hydro-rosconsole
  ros-hydro-realtime-tools
  ros-hydro-roscpp
  ros-hydro-angles
  ros-hydro-catkin
  ros-hydro-tf
  ros-hydro-dynamic-reconfigure)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  tinyxml)

ros_depends=(ros-hydro-rosconsole
  ros-hydro-message-runtime
  ros-hydro-realtime-tools
  ros-hydro-roscpp
  ros-hydro-angles
  ros-hydro-tf
  ros-hydro-dynamic-reconfigure)
depends=(${ros_depends[@]}
  tinyxml)

_tag=release/hydro/control_toolbox/${pkgver}-${_pkgver_patch}
_dir=control_toolbox
source=("${_dir}"::"git+https://github.com/ros-gbp/control_toolbox-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
