# Intermediate R

## CASE WHEN

`SELECT
	-- Select the team long name and team API id
	CASE WHEN  hometeam_id = 10189 THEN 'FC Schalke 04'
    WHEN hometeam_id = 9823 THEN 'FC Bayern Munich'
    ELSE 'Other' END AS home_team,
    COUNT(id) AS total_matches
FROM matches_germany
-- Only include FC Schalke 04 and FC Bayern Munich
GROUP BY home_team; `
