### Gates are automated process for approval

1. Edit previous release pipeline
1. Edit Production stage and add pre-deployment condition (Mouse hover on the Prod stage)
1. Turn On Gates and add a Deployment Gate -> Enable "Query work Items"
1. Create and run Query in Work Items - Boards\Queries\Create\Work Item Type=Bug and Status <> Closed
1. Save query as Shared Query. Name - Active Bugs
1. Open All Shared Queries section. Open More actions (Click ...\More Actions\Security)
1. Search for the <project>-Build Service. Read->Allow
1. Do the same steps for specific query and explicity set Read-> Allow for <project>Build Service
1. Chose the query in Pipeline. Upper threashhold -> 0 for no active bugs. Also set other values for 2-3 min reattempt
1. Save and "Create Release"
1. Edit source code and Commit
1. Wait for another release and you need to give approval
1. Can mouse hover on the stage and click Logs
1. Resolve bugs and then check again if build is success or not.
