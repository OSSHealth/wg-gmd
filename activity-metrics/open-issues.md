# Open Issues

## 1. Description
Number of open issues

## 2. Use Cases

A community manager is interested in understanding how many issues are open on her project at a point in time, and over time. An open issues metric, filtered by 1 week time periods will provide a sense of whether or not the number of open issues is growing, declining or stable. How the community manager interprets that information is highly contextual.  In the case of a new community/project, a lot of open issues may signal engagement from early developers and be viewed as a positive sign.  In the case of a highly stable project that has declined in issue creation over time as it became stable, a sudden spike in issue creation would signal that something may be amiss with the software. 

A Company that funds people to help contribute to a community may want to interpret and make sense of the momementum effects of the resources they are contributing to a project.  Is the addition of two corporate developers to an open source project making that project move through issues faster and more efficiently? 
 
## 3. Sample Filter and Visualization

## 4. Sample Implementation

### [Augur: number of new issues opened each week](https://github.com/OSSHealth/ghdata/blob/master/ghdata/ghtorrent.py)
	- def __single_table_count_by_date(self, table, repo_col='project_id', user_col='author_id', group_by="week"):
	- https://osshealth.github.io/ghdata/api/index.html#api-Timeseries-Issues

### GHTorrent: Number of Open Issues (current)

```SQL
SELECT count(distinct issue_events.issue_id) as num_open_issues, projects.name as project_name, url as url
FROM msr14.issue_events
	join issues on issues.id = issue_events.issue_id
	join projects on issues.repo_id = projects.id
where issue_events.issue_id not in
	(SELECT issue_id FROM msr14.issue_events
	where action = 'closed')
group by projects.id
```

## 5. Known Implementations

## 6. External References (Literature)
