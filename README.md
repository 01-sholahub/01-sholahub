
makeCacheMatrix <- function(x = matrix()) {
  b <- NULL
  set <- function(y){
  x <<- y
  b <<- NULL
  }
  get <- function()x
  setInverse <- function(inverse) b <<- inverse
  getInverse <- function() b 
  list(set = set, get = get, 
  setInverse = setInverse, 
  getInverse = getInverse)
}
