# YogaNarasimhaReddy Peddireddy
##### Kurnool
The original name of Kurnool is found in historical records as **Kandanavolu or Kandanolu**. It used to be a crossing on the Tungabhadra River, where the bullock cart caravans are believed to have greased their wheels **kandana** being a reference to grease. The city is often referred to as **The Gateway of Rayalaseema**. **Belum Caves** are geologically and historically important caves in the district. There are indications that Jain and Buddhist monks were occupying these caves centuries ago. Many Buddhists relics were found inside the caves. These relics are now housed in Museum at **Ananthapur**.

---

#### Directions to the closest Airport to Kurnool

**Rajiv Gandhi International Airpot** is the closest airport to Kurnool where I can find my favorite food

1. Take a free right to the Outer Ring Road
2. Exit Outer Ring Road to NH44 highway 
3. After 30 Kilometers You will enter NH7 
4. You can contiue upto 180 Kilometers on NH7
5. When you are approching Hyderabad you will be able to see direction to enter Nehru Outer Ring Road
6. Take the free left when see the directions on the highway to Nehru Outer ring road.
7. exit the Outer Ring Road on to exit no 18, this will take you to the Airport.

#### Food recomendations for newbies

* Rayalaseema Chicken
* Gongura Chicken
* Chicken Pakoda
* Fast Food at park road


---

#### Sport Recomendations

The below table indicates the sports activity that I would like to recommend others to participate and which is the best place to try and how much it would cost to by the equipment for the sport activity.

| Sport | Location | Equipment Cost |
|:-----:|:--------:|---------------:|
|Cricket|LB Stadium|$10|
|Vollyball|StbcGorund|$30|
|Kabadi|Gachibowli Stadium|$20|
|Football|Mubai Stadium|$20|
 
 ---

#### Quotes

>The greatest religion it to be true to your own nature.<br>
>Have faith in yourselves.<br>
                         *Swami Vivekananda*

>The journey of a thousand miles begins with one step.<br>
                          *Lao Tzu*

>That which does not kill us makes us stronger.<br>
                          *Friedrich Nietzsche*  


---

#### Convex Hull construction

we will discuss the problem of constructing a convex hull from a set of points.<br>

Consider  points given on a plane, and the objective is to generate a convex hull, i.e. the smallest convex polygon that contains all the given points.

[Click here to find the algorithm full discription](https://cp-algorithms.com/geometry/convex-hull.html)
 
Below is the algorithm `Monotone chain Algorithm` chain algorithm published in 1979 by Andrew.<br>

[Click here to find the algorithm in the published website ](https://cp-algorithms.com/geometry/convex-hull.html)

```
struct pt {
    double x, y;
};

int orientation(pt a, pt b, pt c) {
    double v = a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y);
    if (v < 0) return -1; // clockwise
    if (v > 0) return +1; // counter-clockwise
    return 0;
}

bool cw(pt a, pt b, pt c, bool include_collinear) {
    int o = orientation(a, b, c);
    return o < 0 || (include_collinear && o == 0);
}
bool ccw(pt a, pt b, pt c, bool include_collinear) {
    int o = orientation(a, b, c);
    return o > 0 || (include_collinear && o == 0);
}

void convex_hull(vector<pt>& a, bool include_collinear = false) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), [](pt a, pt b) {
        return make_pair(a.x, a.y) < make_pair(b.x, b.y);
    });
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2, include_collinear)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i], include_collinear))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2, include_collinear)) {
            while (down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i], include_collinear))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    if (include_collinear && up.size() == a.size()) {
        reverse(a.begin(), a.end());
        return;
    }
    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}
```

**[Click here to findout about me](https://github.com/yogi4297/assignment2-Peddireddy/blob/main/AboutMe.md#yoganarasimhareddy-peddireddy)**