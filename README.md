# budget-funds
#include <iostream>
using namespace std;
const int N = 510;
int p[N][N];

int dx[] = { 0, 0, 1, -1 }, dy[] = { 1, -1, 0, 0 };
int n, m;
void dfs(int x, int y) {
    for (int i = 0; i < 4; i++) {
        int xx = x + dx[i], yy = y + dy[i];
        if (xx < 0 || xx > n + 1 || yy < 0 || yy > m + 1 || p[xx][yy])
            continue;
        p[xx][yy] = 1;
        dfs(xx, yy);
    }
}
int main() {
    cin >> n >> m;
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++) {
            char c;
            cin >> c;
            if (c == '0')
                p[i][j] = 0;
            else
                p[i][j] = 1;
        }
    dfs(0, 0);
    int z = 0;
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++)
            if (!p[i][j])
                z++;
    cout << z << endl;
    return 0;
}
