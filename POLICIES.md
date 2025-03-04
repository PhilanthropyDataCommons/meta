# Philanthropy Data Commons: Data Management Practices

Documentation of technical policies about data management in the PDC.

## Data Transformation and Deletion

When a given data set is to be transformed in some way -- including
deletion of that data -- our practice is:

* First file a ticket describing the task.  The ticket can be filed
  ([here](https://github.com/PhilanthropyDataCommons/meta/issues), or
  perhaps in the
  [deploy](https://github.com/PhilanthropyDataCommons/deploy/issues)
  or the
  [data-scripts](https://github.com/PhilanthropyDataCommons/data-scripts/issues)
  repository, whichever is most appropriate to the task.

* Assign it to a specific person

* When that person fulfills the task, they should follow up in the
  ticket describing precisely what they did (e.g., by giving a command
  transcript).  It could be that multiple people are involved in
  actually performing the task, but there should still be one assignee
  for the ticket: that's the owner -- the person in charge of making
  sure that the overall task gets completed.

* The description should include a confirmation step.  For example, if
  you deleted all data from a given organization, then show an SQL
  query or an API call whose output demonstrates that there is no data
  from that organization present in the database.

  Remember that there may be multiple copies of a data set: e.g., in
  staging databases as well as production, in individual developers'
  development environments, etc.  Depending on the task, all of those
  copies may need to be tracked down and transformed or deleted.

If there is anything confidential or sensitive about a task, then the
ticket can be filed in an internal tracker at the developer's
organization, but otherwise the rest of this policy still applies.
