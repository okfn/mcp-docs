# No accounts, no database

The pilot runs without user accounts and without a database. Users do not
register, so we cannot save or share whole conversations. What you can do
is download individual pieces: a table, a chart, or one of the AI's
answers.

## The trade-off

This is a deliberate design choice, and it cuts both ways.

- **The benefit:** the system stays very simple and very easy to install.
  There is no database to run, back up or secure, and no personal data to
  look after.
- **The cost:** conversations cannot be saved or shared, and you cannot
  download a full answer (prose plus tables plus charts) in one go, only
  the pieces.

For a pilot, simplicity won, and nothing in the feedback made us regret
it. If a future deployment needs saved or shared conversations, that is
the point at which adding storage would be worth its extra weight.
