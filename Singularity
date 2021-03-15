BootStrap: shub
From: willgpaik/centos8_roar
%setup

%files

%environment 

%runscript


%post
    # commands to be executed inside container during bootstrap
    # add python and install some packages
    dnf update -y
    dnf install -y vte291-devel
    dnf install -y vte-profile
    dnf -y groups install "Development Tools"
    dnf -y groups install "Base"
    dnf -y install git cmake gcc-c++ gcc binutils \
	libX11-devel libXpm-devel libXft-devel libXext-devel
    dnf -y install gcc-gfortran openssl-devel pcre-devel \
	mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
	fftw-devel cfitsio-devel graphviz-devel \
	avahi-compat-libdns_sd-devel openldap \
	libxml2-devel gsl-devel
    dnf -y install openmpi-devel
    dnf -y install cmake3
    dnf -y install hdf5-devel
    dnf -y install patch
    dnf -y install git zlib-devel libtiff-devel
    # qgis dependencies: https://github.com/qgis/QGIS/blob/master/INSTALL.md#3-building-on-gnulinux
    dnf -y install proj-devel libspatialite-devel qwt-qt5-devel expat-devel qca-qt5-devel libzip-devel
    # Required by GRASS 7.8.5
    dnf -y install python3-wxpython4
    pip3 install wxPython
    

    # Install GRASS 7.8.5
    # First install these three dependencies:
    # https://copr.fedorainfracloud.org/coprs/neteler/python-matplotlib/
    #dnf -O /etc/yum.repos.d/python-matplotlib.repo https://copr.fedoraproject.org/coprs/neteler/python-matplotlib/repo/epel-7/neteler-python-matplotlib-epel-7.repo
    # install qhull dependency from EPEL7
    #dnf -y install qhull
    # now install this package
    #dnf -y install python-matplotlib
    # https://copr.fedorainfracloud.org/coprs/neteler/liblas/
    #dnf -y install liblas liblas-devel
    # https://copr.fedorainfracloud.org/coprs/neteler/laszip/
    #dnf -y install laszip-devel
    
    # Then install GDAL from EPEL
    dnf -y install gdal gdal-python-tools gdal-devel
    
    # Now install GRASS GIS 7:
    #wget -O /etc/yum.repos.d/grass78.repo https://copr.fedoraproject.org/coprs/neteler/grass78/repo/epel-7/neteler-grass78-epel-7.repo
    dnf -y update
    #dnf -y install grass grass-libs grass-gui liblas
    # needed for GRASS Addons (via g.extension)
    dnf -y install grass-devel vblas-devel
    
    # To fix issue with "libpq-fe.h not found" and "geos_c.h" not found
    dnf -y install postgresql-devel
    dnf -y install geos-devel
    
    # Install QGIS
#    rpm -Uvh http://elgis.argeo.org/repos/5/elgis-release-5-5_0.noarch.rpm
    dnf copr enable dani/qgis
    dnf -y install qgis-devel
    dnf -y install python3-qgis
    dnf install qgis-grass
    dnf -y update
    
    
