# connect_friends
Connect nodes by common friends in R

```
connect_friends<-function(edgelist){
  g <- graph.data.frame(edgelist, directed = T)
  g <- delete_vertices( g, 
                        (!V(g) %in% c(V(g)[[degree(g, mode = "in")>=2]])) & 
                          (!V(g) %in% c(V(g)[[degree(g, mode = "in")==0]])))
 el <- as.data.frame(get.edgelist(g))
  ids <- unique(c(el$V1, el$V2))
  
  y <- lapply(ids, function(id) {
    
    x <- el[which(el$V1 == id | el$V2 == id),]
    alt_nodes <- setdiff(unique(c(x$V1, x$V2)), id)
    
  })
  
  if(length(y)==0) {
    stop("No common friends found")
  }
  ne2=NULL
  ne=NULL
  for (i in 1:length(y)) {
    new_edge <- y[[i]]
    if (length(new_edge)>=2){
      ne <- t(combn(new_edge,2))
    }
    ne2 <- rbind(ne,ne2)
  }
  g2  <<-  graph.data.frame(ne2, directed  =  F)
  
}

