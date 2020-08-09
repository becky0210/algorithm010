Unique-paths-ii state transition equation

    if(obstacleGrid[i][j]==0)
        dp[i][j]=i-1>=0?dp[i-1][j]:0+j-1>=0?dp[i][j-1]:0;
    else
        dp[i][j]=0;
