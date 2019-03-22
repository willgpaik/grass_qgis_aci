# grass_qgis_aci
Singularity recipe for GRASS GIS and QGIS on Centos 7 For ICS ACI clusters

2019/1/22  
GRASS 7.4.4 is updated

2019/1/25  
GRASS GIS g.extension function can be used by:  
```
$ grass74 /PATH/to/Mapset/PERMANENT --exec g.extension <ADD-ON>
```

If Mapset is not installed, download sample Mapset to "scratch" directory:
```
$ cd ~/scratch
$ wget https://grass.osgeo.org/sampledata/worldlocation.tar.gz
$ tar -xf worldlocation.tar.gz
    
$ grass74 ~/scratch/worldlocation/PERMANENT --exec g.extension <ADD-ON>
```
To delete sample Mapset:
```
$ cd ~/scartch
$ rm -rf worldlocation
$ rm worldlocation.tar.gz
```
