This repo contains the following MOOS-IvP processes:

--------------------------------------------------------------------------------

pLonLatToWptUpdate: 
  convert a comma-colon separated list of longitude-latitude waypoints into
  x,y waypoints

--------------------------------------------------------------------------------

pPublishAfterX:
  publish a specified var-val pair X MOOS seconds after another specified
  var-val pair was published

--------------------------------------------------------------------------------

uSimBioSensor:
  a simple simulation of a point sensor, e.g. temperate, chlorophyll
  It requires a .csv file that has the actual data in it, 
  and assumes a data grid, from where it indexes to find the current data point.
  in 2D: lon, lat, data
  in 3D: lon, lat, depth, data
  
  Gaussian sensor noise can be added.
  
  Example first couple lines of the CSV:
  3D:
lon_min,lon_max,lon_res,lat_min,lat_max,lat_res,depth_min,depth_max,depth_res
-117.809665,-117.805330,41.000000,34.087454,34.089286,21.000000,0,-15,31
lon,lat,depth,data
-117.809665,34.087454,0.500000,4.157393
...

  2D:
lon_min,lon_max,lon_res,lat_min,lat_max,lat_res
-117.809665,-117.80533,41.0,34.087454,34.089286,21.0
lon,lat,data
-117.809665,34.087454,14.1872410919
...

  Note that lon_res and lat_res are the number of vertices in the grid.
  (vertices = number of edges + 1)
  For a 400x200 meter area, with 10m grid spacing, this is 41x21.

--------------------------------------------------------------------------------
