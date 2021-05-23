# connect_friends
Connect nodes by common friends in R

Given an edgelist of nodes (directed), the function connects nodes if they share a common friend.

# Example:

<details open="open">
  <summary><h2 style="display: inline-block">Load the edgelist </h2></summary>

  `edgelist <- read.table(text = "
                       A C
                       B C
                       D C
                       E F
                       G F
                       H F
                       I J
                       I K")`

`g <- graph.data.frame(edgelist, directed = T)`
  

  <img src="https://user-images.githubusercontent.com/62380208/119257911-b6853000-bbc7-11eb-8d02-2d26253fcaf7.png" width="200" height="200"/>
  
  
  In this case we would like nodes A,B,D and G,H,E to be connected as they share a common friend.
  


<details open="open">
  <summary><h2 style="display: inline-block">Use function </h2></summary>

`connect_friends(edgelist)`

`plot(simplify(g2),edge.arrow.size=0.01,vertex.size=3,
     display.isolates=FALSE,vertex.label=NA)`
  

  <img src="https://user-images.githubusercontent.com/62380208/119257938-db79a300-bbc7-11eb-8e1b-3a0806b66951.png" width="200" height="200"/>




