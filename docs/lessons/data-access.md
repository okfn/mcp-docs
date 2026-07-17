# New tools, old problems

Connecting an AI to an open data portal is a shiny new tool, but it
drags in a set of very old data-governance questions. None of them are
about AI; all of them decide whether the answers can be trusted.

- **Direct access or a read copy?** Do the tools read the open data
  directly from the portal, or a separate read-only copy? Each choice
  has consequences for freshness and for load on the portal.
- **The data, or a view of it?** Are we serving the raw dataset or some
  transformed view of it, and is that transformation documented?
- **Is it the latest version?** A cached or copied dataset can quietly
  fall behind the source. An answer from stale data is still wrong.
- **Are we inflating the portal's statistics?** If every query hits the
  open data endpoint, we may be distorting the portal's own usage
  metrics just by reading data to answer questions.
- **What business rules are baked into the data?** Datasets are produced
  with assumptions and rules embedded in them. Those rules often need to
  be explained to the user, or the number is easy to misread.

The lesson is not to solve all of these at once, but to decide each one
deliberately for your deployment, and to write the decision down. New
tools do not excuse you from the old questions.
