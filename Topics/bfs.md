# Breadth-First Search

DFS traverses the *width* of a graph before the depth. Think of it as traversing in layers.

<details>
	<summary>Examples</summary>

Given a binary square matrix, find the shortest path from one corner (0,0) to the other (n-1,n-1).
```java
// java 

class Solution {
    
    static final int inf = -1;	// Can also set this to a rly large num

	// Movements are up, down, left, right, and diagonally
	static final int[] xmove = {-1, 1, -1, 1, -1, 1, 0, 0};
	static final int[] ymove = {-1, 1, 1, -1, 0, 0, -1, 1};
    
    
    public int shortestPathBinaryMatrix(int[][] grid) {
        int length = grid.length;
        int width = grid[0].length;
        

        // The dist matrix keeps track of the shortest path to each cell
        int[][] dist = new int[length+1][width+1];
        for(int i=0; i<length; i++) {
            for(int j=0; j<width; j++) dist[i][j] = inf;
        }
        dist[0][0] = 1;     // Start point takes 0 or 1 move(s) to get to itself
        

        if(grid[0][0] == 1 || grid[length-1][width-1] == 1) {   // Checks to see if the start or end are blocked
            return(-1);
        }
        else {
            Queue<Integer> q = new LinkedList<Integer>();
            q.add(0); q.add(0);     // Add start point into queue

            while(!q.isEmpty()) {     // Dequeue a cell in the current layer
                int x = q.remove();
                int y = q.remove();

                for(int i=0; i<xmove.length; i++) {     // For each movement option...
                    int xx = x + xmove[i];
                    int yy = y + ymove[i];

                    // ...Check to see if it's in bounds...
                    if(xx >= 0 && yy >= 0 && xx < length && yy < width) {
                        
                    	// ...If the end is reached, return how many moves it took to get there
                        if(xx == length-1 && yy == width-1) {
                            dist[xx][yy] = dist[x][y] + 1;
                            return(dist[xx][yy]);
                        } 

                        // ...Otherwise, check to see if the cell is open
                        else if(grid[xx][yy] == 0) {
                            int tmp = dist[x][y] + 1;
                            if(dist[xx][yy] == inf) {     // If the cell has not yet been visited...
                                dist[xx][yy] = tmp;
                                q.add(xx);
                                q.add(yy);     // ...Enqueue the cell as part of the next layer
                            }
                        }
                    }
                }
            }
          	
            return(dist[length-1][width-1]);     // Returns -1 if the end is unreachable, or 1 for a 1x1 matrix
        }
    }
}
```

</details>