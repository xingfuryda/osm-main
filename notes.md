Docker images

	• osm-store      PostgreSQL with PostGIS - stores result of pbf import
	• osm-load       Osm2pgsql - converts pbf to pgsql
	• osm-style      Mapbox Studio Classic - for authoring tmstyle and tmsource projects

Docker compose notes

	• $ ./docker build -t xingfuryda/osm-store osm-store                will build an image
	• $ ./docker-compose.exe -f osm-main/docker-compose.yaml rm --all   will remove all compose containers
	• $ ./docker-compose.exe -f osm-main/docker-compose.yaml up         starts all in compose file
	• $ ./docker-compose.exe -f osm-main/docker-compose.yaml run load help      runs the help command in the load compose service
	• $ ./docker rmi -f $(./docker images -f "dangling=true" -q)                 clean '<none>' images
	• $ ./docker images -q | xargs ./docker rmi -f                      delete all images from a machine
	• $ ./docker-machine ssh default -L 3000:localhost:3000 -L 8080:localhost:8080            ssh port forward so you can access service from localhost
	• $ ./docker-machine rm default                                    remove a docker machine
	• $ ./docker-machine create -d virtualbox --virtualbox-memory 4096 default      create a docker maachine with 4GB ram
	
	
./docker build -t xingfuryda/osm-store osm-store && ./docker build -t xingfuryda/osm-load osm-load && ./docker build -t xingfuryda/osm-style osm-style

http://tools.geofabrik.de/

Hawaii export

/home/root/mapbox-studio-classic/node_modules/.bin/tilelive-copy \
--scheme=pyramid \
--bounds=-166.51,14.58,-148.94,27.07 \
--minzoom=0 \
--maxzoom=16 \
bridge:///home/root/projects/openstreetmap-carto.tm2source/data.xml \
mbtiles:///home/root/projects/out.mbtiles

Copying installed fonts

cp -r /usr/share/fonts/ /home/root/projects/fonts/

source for tm2 project.yaml for when hosting mbtiles from tessera:
source: http://localhost:8080/pbfs/live/index.json