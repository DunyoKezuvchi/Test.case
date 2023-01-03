#include<bits/stdc++.h>
#define int long long
using namespace std;
int func(int n, int a[]){
    int  p[n+1];
    p[0] = 0;
    for (int i = 1; i <= n; i++) {
        p[i] = p[i-1] + a[i];
    }

    map < int, int > mp;
    for (int i = 0; i <= n; i++) {
        if (mp.find(p[i]) != mp.end()) {
            mp[p[i]]++;
        }
        else mp[p[i]] = 1ll;
    }
    int s = 0ll;
    for (auto & [k, v] : mp) {
        s += (v * (v - 1ll) / (2ll));
    }
    return s;

}
signed main() {
    int t = 200;
    for(int i=1; i <=t ; i++){
        string in, ou;
        in = "00" + to_string(i) + ".in";
        ou = "00" + to_string(i) + ".out";
        while (in.size() > 6) {
            in.erase(0, 1);
            ou.erase(0, 1);
        }
        ofstream out(ou);
        ofstream inn(in);

        int n = rand()%1000000 + 1;
        inn << n << endl;
        int a[n];
        for (int i=0; i < n; i++){
            a[i] = pow(-1, rand() % 2) * (rand() % 10ll);
            inn << a[i] << ' ';
        }
        out << func(n,a) << endl;
        inn.close();
        out.close();
    }
    return 0;
}
