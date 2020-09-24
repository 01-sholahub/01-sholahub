
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


cacheSolve <- function(x, ...) {
## Return a matrix that is the inverse of 'x'
  b <- x$getInverse()
  if(!is.null(b)){
  message("getting cached data")
  return(b)
  }
  mat <- x$get()
  b <- solve(mat,...)
  x$setInverse(b)
  b




Checking the program------------------------
b <- matrix(rnorm(16),4,4)
b1 <- makeCacheMatrix(b)
cacheSolve(b1)
[,1] [,2] [,3] [,4]
[1,] -0.1653269 0.2592203 0.6176218 -0.7520955
[2,] 0.2828334 -0.1853499 0.4511382 0.2094365
[3,] 0.1434840 1.0413868 -0.3550853 -0.3261154
[4,] 0.1793583 -0.4252171 -0.4371493 -0.1749830



testing my function

source("ProgrammingAssignment2/cachematrix.R")
my_matrix <- makeCacheMatrix(matrix(1:4, 2, 2))
my_matrix$get()
[,1] [,2]
[1,] 1 3
[2,] 2 4
my_matrix$getInverse()
NULL
cacheSolve(my_matrix)
[,1] [,2]
[1,] -2 1.5
[2,] 1 -0.5
cacheSolve(my_matrix)
getting cached data
[,1] [,2]
[1,] -2 1.5
[2,] 1 -0.5
my_matrix$getInverse()
[,1] [,2]
[1,] -2 1.5
[2,] 1 -0.5
my_matrix$set(matrix(c(2, 2, 1, 4), 2, 2))
my_matrix$get()
[,1] [,2]
[1,] 2 1
[2,] 2 4
my_matrix$getInverse()
NULL
cacheSolve(my_matrix)
[,1] [,2]
[1,] 0.6666667 -0.1666667
[2,] -0.3333333 0.3333333
cacheSolve(my_matrix)
getting cached data
[,1] [,2]
[1,] 0.6666667 -0.1666667
[2,] -0.3333333 0.3333333
my_matrix$getInverse()
[,1] [,2]
[1,] 0.6666667 -0.1666667
[2,] -0.3333333 0.3333333


