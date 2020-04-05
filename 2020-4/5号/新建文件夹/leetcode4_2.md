给定一个二维矩阵，计算其子矩形范围内元素的总和，该子矩阵的左上角为 (row1, col1) ，右下角为 (row2, col2)。

<img src="https://assets.leetcode-cn.com/aliyun-lc-upload/images/304.png" alt="Range Sum Query 2D" style="zoom:67%;" />




上图子矩阵左上角 (row1, col1) = (2, 1) ，右下角(row2, col2) = (4, 3)，该子矩形内元素的总和为 8。

示例:

给定 matrix = [
  [3, 0, 1, 4, 2],
  [5, 6, 3, 2, 1],
  [1, 2, 0, 1, 5],
  [4, 1, 0, 1, 7],
  [1, 0, 3, 0, 5]
]

sumRegion(2, 1, 4, 3) -> 8
sumRegion(1, 1, 2, 2) -> 11
sumRegion(1, 2, 2, 4) -> 12
说明:

你可以假设矩阵不可变。
会多次调用 sumRegion 方法。
你可以假设 row1 ≤ row2 且 col1 ≤ col2。

```c++
class NumMatrix {
public:
	vector<vector<int>> memory;
	NumMatrix(vector<vector<int>>& matrix) {
		if (matrix.size() < 1) {
			return;
		}
		memory = vector<vector<int>>(matrix.size() + 1, vector<int>(matrix[0].size() + 1, 0));
		for (int i = 0; i < matrix.size(); i++) {
			for (int j = 0; j < matrix[0].size(); j++) {
				memory[i + 1][j + 1] = memory[i + 1][j] + memory[i][j + 1] - memory[i][j] + matrix[i][j];
			}
		}
	}

	int sumRegion(int row1, int col1, int row2, int col2) {
		if (row1 < 0 || col1 < 0 || row2 + 1 >= memory.size() || col2 + 1 >= memory[0].size()) {
			return 0;
		}
		int result = memory[row2 + 1][col2 + 1] - memory[row1][col2 + 1] - memory[row2 + 1][col1] + memory[row1][col1];
		return result;
	}
};

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix* obj = new NumMatrix(matrix);
 * int param_1 = obj->sumRegion(row1,col1,row2,col2);
 */
```

