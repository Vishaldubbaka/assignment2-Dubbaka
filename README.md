# assignment2-Dubbaka

# Vishal Reddy Dubbaka

#### Australia
I'm captivated to the city's thriving art scene and attractive laid-back vibe,
as well as the cultural mix of its residents and their **welcoming friendliness**
are the reasons i like **australia**.

---

# Directions for travelling from Maryville to Australia
1. Book a cab from Maryville to Kansas city
2. Do the web check-in online   
    1. Take the boarding pass from the kiosk
    2. Drop the baggage 
    3. Board the flight
    4. Arrive at the destination 
3. Complete check-out in Sydney,Australia

* Clothing
    * Jacket
    * Jeans
    * Flipflops
    * Shoes

* Camera Equipment
    * Tripod
    * Camera
    * Gopro
    * Extra batteries

* Cash

[AboutMe](https://github.com/Vishaldubbaka/assignment2-Dubbaka/blob/main/AboutMe.md)

---

# Table creation

The table below recommends some of the best foods that i had in India with prices and locations.

|  FOOD/DRINK    |    LOCATION   |    PRICE   |
|     ---        |      ---      |     ---    |
|Mutton Biryani  |  Shah ghouse  |   $8 .00   |
|Pathar ka ghosht|   Chichas     |   $12.00   |
|Malai Lassi     |  Pathabasthi  |   $2 .00   |
|Tea             |  Nimrah Cafe  |   $1 .00   |

---

# Quotes by Authors that I like

> "Money is not everything,but make sure you earn a lot before speaking such nonsense." - by
***Warren Buffett*** <br>
> "In each of us there is another,whom we do not know." - by
***Carl Jung*** 

# Code fencing (Dynamic processing)
Dynamic programming is both a mathematical optimization method and a computer programming method. The method was developed by Richard Bellman in the 1950s and has found applications in numerous fields, from aerospace engineering to economics. <https://en.wikipedia.org/wiki/Dynamic_programming>

```
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}
```

<https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html>
