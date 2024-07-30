# MONDAY
REPO
7.Write Prolog Program for Travelling Sales Man Problem.
 % Define the cities and their distances distance(city1, city2, 10).
 distance(city1, city3, 15). 
distance(city1, city4, 20).
 distance(city2, city3, 35).
 distance(city2, city4, 25). 
distance(city3, city4, 30).
 % Define the predicate to find the shortest path
 tsp(ShortestPath, ShortestDistance) :- findall(Path, permutation([city1, city2, city3, city4], Path), Permutations), 
findall([Distance, Path], (member(Path, Permutations), path_distance(Path, Distance)), Paths), sort(Paths, SortedPaths), SortedPaths = [[ShortestDistance, ShortestPath]|_].
 % Define the predicate to calculate the distance of a path
 path_distance([City], 0).
 path_distance([City1, City2|Rest], Distance) :- distance(City1, City2, Dist1), path_distance([City2|Rest], Dist2), Distance is Dist1 + Dist2. 

% Define the permutation predicate (built-in in SWI-Prolog) permutation([], []). 

permutation(List, [H|Perm]) :- select(H, List, Rest), permutation(Rest, Perm). 
% Define the select predicate (built-in in SWI-Prolog) select(X, [X|Xs], Xs). select(X, [Y|Ys], [Y|Zs]) :- select(X, Ys, Zs).
 OUTPUT :  ?-  tsp(ShortestPath, ShortestDistance). 
ShortestPath = [city1, city2, city3, city4], ShortestDistance = 75. 
