
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
    yum install -y epel-release
    yum install -y terminator
    yum install -y centos-release-scl
    yum install -y vte-devel
    yum install -y vte291-devel
    yum install -y vte-profile
    yum install -y devtoolset-7-gcc*
    scl enable devtoolset-7 bash
    yum -y groups install "Development Tools"
    yum -y groups install "Base"
    yum -y install git cmake gcc-c++ gcc binutils \
	libX11-devel libXpm-devel libXft-devel libXext-devel
    yum -y install gcc-gfortran openssl-devel pcre-devel \
	mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
	fftw-devel cfitsio-devel graphviz-devel \
	avahi-compat-libdns_sd-devel libldap-dev python-devel \
	libxml2-devel gsl-devel
    yum -y install openmpi-devel
    yum -y install cmake3
    yum -y install hdf5-devel
#    yum -y install boost-devel
    yum -y install patch
    yum -y install git g++ zlib-devel libqt4-devel libgl1-mesa-dev libtiff-devel
    # Required by GRASS 7.8.3
    yum -y install wxPython-devel python2-pip
    pip2 install wxPython
    pip3 install wxPython
    

    # Install GRASS 7.8.3
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
    wget -O /etc/yum.repos.d/grass78.repo https://copr.fedoraproject.org/coprs/neteler/grass78/repo/epel-7/neteler-grass78-epel-7.repo
    yum -y update
    yum -y install grass grass-libs grass-gui liblas
    # needed for GRASS Addons (via g.extension)
    yum -y install grass-devel liblas liblas-devel
    
    # To fix issue with "libpq-fe.h not found" and "geos_c.h" not found
    yum -y install postgresql-devel
    yum -y install geos-devel
    
    # Install QGIS
#    rpm -Uvh http://elgis.argeo.org/repos/5/elgis-release-5-5_0.noarch.rpm
    yum -y install qgis-devel
    yum -y update
    
    
#    mkdir -p /storage/home
#    mkdir -p /storage/work
#    mkdir -p /gpfs/scratch
#    mkdir -p /gpfs/group
    
#    mkdir -p /gpfs/scratch/test
#    cd /gpfs/scratch
#    wget https://grass.osgeo.org/sampledata/worldlocation.tar.gz
#    tar -xf worldlocation.tar.gz
    
#    grass78 /gpfs/scratch/worldlocation/PERMANENT --exec g.extension r.accumulate r.snap.stream r.cell.area
    
#    rm -rf worldlocation
#    rm worldlocation.tar.gz
    
    
