
## notes from 10-Nov-2017 meeting

### current problems:
1. different people/groups have different way of working with/developing sprocs (testing strategy, answers to 'where does the truth live?')
1. no way to know what procs are system-specific, which are client-speicific
1. no way to determ dependencies between procs
1. no automated testing being done on many(most?) sprocs (TSQL-T)

### some thoughts on "solving" or at least not continuing these:
* Management of SQL Stored Procedures - 
  * a workflow that makes sure all code is kept in a visible repository with good commit messages?
  * a workflow that makes sure all code is compiled to the database and has a good change comment? 
* if there is a degree of quality separation, it's between 
  * sprocs that are for one client only (lower-quality??) 
  * those that are 'part of the system' or 'part of a toolkit' (high quality?)
* there is currently no naming convention. It would be difficult/dangerous to try to retrofit a convention to existing code, but desirable to create a convention and insist on using it for new code; strongly encourage using it whenever making changes to existing code. 
  * example: `navs_*` (system) & `navc_*` (customer-specific)
  * naming convention for what? i.e. is naming the right place to solve the problem?  (what is the problem? discussion reflected in 'current problems' section above)
  * currently grouped somewhat by function then client?
* no sproc with many multiple client-specific sections
  * small, single-purpose procedures 
  * table-driven (ie. client 12 -> navs_fooA, client 44 -> navs_fooB)
* general guidelines for SQL quality 
  * no cursors (i.e. favor set-basd processing over row-based processing)
  * no use of `SELECT *`

### next steps: 
1. get a good story for source control going (DL to propose a workflow)
1. ?
1. profit! 
