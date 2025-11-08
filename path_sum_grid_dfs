"""
Path Sum in Grid using DFS (Up, Down, Left, Right only)

Finds a path from (0,0) to (n-1,n-1) in an n×n grid such that:
- Allowed moves: Up, Down, Left, Right
- Diagonal movement NOT allowed
- Path cannot revisit a cell (prevent loops)
- Total sum of visited cells must equal K

Author: Samin
"""

def find_path_with_sum(grid, K):
    n = len(grid)
    visited = [[False] * n for _ in range(n)]
    path = []

    # Allowed movements (no diagonals)
    moves = [(1,0), (-1,0), (0,1), (0,-1)]

    def dfs(i, j, current_sum):
        # Out of grid
        if i < 0 or j < 0 or i >= n or j >= n:
            return False

        # Already visited → loop
        if visited[i][j]:
            return False

        new_sum = current_sum + grid[i][j]

        # Prune if sum is too large
        if new_sum > K:
            return False

        # Mark
        visited[i][j] = True
        path.append((i, j))

        # Destination reached
        if i == n - 1 and j == n - 1:
            if new_sum == K:
                return True

        # Explore neighbors
        for di, dj in moves:
            if dfs(i + di, j + dj, new_sum):
                return True

        # Backtrack
        visited[i][j] = False
        path.pop()
        return False

    # Start DFS from (0,0)
    if dfs(0, 0, 0):
        return path
    else:
        return None


# -------------------------
# Example usage
# -------------------------

if __name__ == "__main__":
    grid = [
        [1, 3, 2],
        [4, 6, 1],
        [1, 1, 5]
    ]

    K = 12

    print("Grid:")
    for row in grid:
        print(row)

    print("\nTarget Sum:", K)
    result = find_path_with_sum(grid, K)

    if result:
        print("\nPath Found:")
        print(result)
    else:
        print("\nNo path exists with sum =", K)
