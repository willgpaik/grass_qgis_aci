
BootStrap: docker
From: centos:centos7
%setup

%files

%environment 

%runscript


%post
    # commands to be executed inside container during bootstrap
    # add python and install some packages
    yum update -y
    yum install -y epel-release \
    terminator \
    centos-release-scl \
    vte-devel \
    vte291-devel \
    vte-profile \
    devtoolset-7-gcc*
    yum -y groups install "Development Tools"
    yum -y groups install "Base"
    yum -y install git \
    	cmake \
    	gcc-c++ \
	gcc \
	binutils \
	libX11-devel \
	libXpm-devel \
	libXft-devel \
	libXext-devel \
  	gcc-gfortran \
	openssl-devel \
	pcre-devel \
	mesa-libGL-devel \
	mesa-libGLU-devel \
	glew-devel \
	ftgl-devel \
	mysql-devel \
	fftw-devel \
	cfitsio-devel \
	graphviz-devel \
	avahi-compat-libdns_sd-devel \
	libldap-dev \
	python-devel \
	libxml2-devel \
	gsl-devel \
	openmpi-devel \
	cmake3 \
	hdf5-devel \
	boost-devel \
    	patch \
    	git \
	g++ \
	zlib-devel \
	libqt4-devel \
	libgl1-mesa-dev \
	libtiff-devel
    scl enable devtoolset-7 bash

    # Install GRASS 7.4.4
    # First install these three dependencies:
    # https://copr.fedorainfracloud.org/coprs/neteler/python-matplotlib/
    	wget -O /etc/yum.repos.d/python-matplotlib.repo https://copr.fedoraproject.org/coprs/neteler/python-matplotlib/repo/epel-7/neteler-python-matplotlib-epel-7.repo
    	# install qhull dependency from EPEL7
	yum -y install qhull
	# now install this package
	yum -y install python-matplotlib
    # https://copr.fedorainfracloud.org/coprs/neteler/liblas/
    	yum -y install liblas liblas-devel
    # https://copr.fedorainfracloud.org/coprs/neteler/laszip/
    	yum -y install laszip-devel
    #
    # Then install GDAL from EPEL
    yum -y install gdal gdal-python gdal-devel
    #
    # Now install GRASS GIS 7:
    wget -O /etc/yum.repos.d/grass74.repo https://copr.fedoraproject.org/coprs/neteler/grass74/repo/epel-7/neteler-grass74-epel-7.repo
    yum -y update
    yum -y install grass grass-libs grass-gui liblas
    # needed for GRASS Addons (via g.extension)
    yum -y install grass-devel liblas liblas-devel
    
    # To fix issue with "libpq-fe.h not found" and "geos_c.h" not found
    yum -y install postgresql-devel
    yum -y install geos-devel
    
    # Install QGIS
    rpm -Uvh http://elgis.argeo.org/repos/5/elgis-release-5-5_0.noarch.rpm
    yum -y install qgis-devel
    yum -y update
    
    
    mkdir -p /storage/home
    mkdir -p /storage/work
    mkdir -p /gpfs/scratch
    mkdir -p /gpfs/group
    
#    mkdir -p /gpfs/scratch/test
#    cd /gpfs/scratch
#    wget https://grass.osgeo.org/sampledata/worldlocation.tar.gz
#    tar -xf worldlocation.tar.gz
    
#    grass74 /gpfs/scratch/worldlocation/PERMANENT --exec g.extension r.accumulate r.snap.stream r.cell.area
    
#    rm -rf worldlocation
#    rm worldlocation.tar.gz
    
    
