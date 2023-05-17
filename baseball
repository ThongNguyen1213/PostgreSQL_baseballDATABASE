-- 1 Heaviest Hitters
SELECT batting.yearid AS "Year", ROUND(AVG(people.weight), 2) AS "Avg weight", teams.name AS "Team name"
FROM batting
	INNER JOIN people
  	ON batting.playerid = people.playerid
  INNER JOIN teams
  	ON batting.teamid = teams.teamid
GROUP BY 1, 3
ORDER BY 1 DESC, 2 DESC

-- 2 Shortest Sluggers
SELECT batting.yearid AS "Year", ROUND(AVG(people.height), 2) AS "Avg height", teams.name AS "Team name"
FROM batting
	INNER JOIN people
  	ON batting.playerid = people.playerid
  INNER JOIN teams
  	ON batting.teamid = teams.teamid
GROUP BY 1, 3
ORDER BY 1 DESC, 2

-- 3 Biggest Spender

SELECT SUM(salary) AS sum, salaries.yearid AS year, teams.name AS team
FROM salaries
 INNER JOIN teams
	ON teams.teamid = salaries.teamid
GROUP BY 2, 3
ORDER BY 2 DESC, 1 DESC

-- 4 Most Bang For Their Buck in 2010
SELECT salaries.yearid AS "Year", teams.name AS "Team", teams.w AS "Win", ROUND(SUM(salary)/teams.w) AS "Cost Per Game"
FROM salaries
 INNER JOIN teams
	ON teams.teamid = salaries.teamid
  AND teams.yearid = salaries.yearid
WHERE salaries.yearid = 2010
GROUP BY 1, 2, 3
ORDER BY 4 DESC

-- 5 Priciest Starter
SELECT salaries.yearid, 
		people.namefirst, 
		people.namelast,
    ROUND(salaries.salary/pitching.g) AS "Cost Per Game",
		pitching.gs AS "Game Started"
FROM salaries
	INNER JOIN people
  	ON people.playerid = salaries.playerid
  INNER JOIN pitching
  	ON people.playerid = pitching.playerid
    AND salaries.yearid = pitching.yearid
    AND salaries.teamid = pitching.teamid
WHERE pitching.gs >= 10
GROUP BY 1, 2, 3, 4, 5
ORDER BY 1 DESC, 4 DESC

