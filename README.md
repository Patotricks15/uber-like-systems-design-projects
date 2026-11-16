# Uber-like Systems Design Projects

A portfolio of independent, production-style projects on the routing and pricing stack of a ride-hailing platform: street-graph routing, driver repositioning, demand forecasting, price elasticity, and surge pricing.

Each project is its own GitHub repository with a reproducible pipeline, offline tests, an executed notebook with figures, and a README that states its data, method, and limitations. Shared map and graph helpers live in `routes-pricing-shared`, pinned by tag `v0.2.0`.

## Projects

| # | Name | Dataset | Main method | Repository |
|---|------|---------|-------------|-------------|
| 1 | Street Graph Routing | OpenStreetMap drive graph (Manhattan) | Dijkstra and A* with haversine heuristic, checked against `networkx` | [street-graph-routing-osmnx](https://github.com/Patotricks15/street-graph-routing-osmnx) |
| 2 | Driver Repositioning Recommender | PR01 forecast on the OSM graph | Top-demand geohash cells, shortest route to the nearest one | [driver-repositioning-recommender](https://github.com/Patotricks15/driver-repositioning-recommender) |
| 3 | Geohash Demand Forecast | Uber Pickups NYC (2014) | XGBoost with lag and POI features, `RandomizedSearchCV` | [geohash-demand-forecast-xgboost](https://github.com/Patotricks15/geohash-demand-forecast-xgboost) |
| 4 | Price Elasticity Log-Log | Uber & Lyft Cab Prices (Boston quotes) | Log-log regression with HC3 robust standard errors | [price-elasticity-loglog](https://github.com/Patotricks15/price-elasticity-loglog) |
| 5 | Surge Multiplier Heatmap | PR01 predictions | Capped, gated surge rule smoothed into a demand-weighted heatmap | [surge-multiplier-heatmap](https://github.com/Patotricks15/surge-multiplier-heatmap) |

## Not yet built

- **ETA Travel Time (LightGBM)** and **GPS Map Matching (HMM)**: the data needs verification first.
- **Pricing A/B Test with CUPED**: design only. No public dataset has arm assignment, so it needs real experiment logs.

## Key limitations

- Projects 3 and 5 use NYC data. Project 4 uses Boston quotes, not completed trips, and its elasticity is weakly identified.
- The data has no driver supply, so the surge multiplier uses a demand-history proxy.
- Driver positions in project 2 are simulated. The routing is real.

## Scope

This is part of an 8-repository plan. Projects are added here as they are completed; each repository listed above is self-contained and can be cloned, tested, and run independently.
