
makeVector <- function(x = numeric()) {
        b <- NULL
        set <- function(y) {
                x <<- y
                b <<- NULL
        }
        get <- function() x
        setmean <- function(mean) b <<- mean
        getmean <- function() m
        list(set = set, get = get,
             setmean = setmean,
             getmean = getmean)
}
