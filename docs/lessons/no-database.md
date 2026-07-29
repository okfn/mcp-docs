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

For a pilot, simplicity won, but the cost side was the most repeated
product complaint in the feedback. Testers compare the chat with the
tools they use every day, ChatGPT or Gemini, and against that reference
the missing history and sharing are felt immediately.

Two things to keep in mind when weighing that complaint. Being a full
chat product was never in the pilot's scope. And the chat gateway is
only one client: the MCP server speaks the standard protocol, so it can
be plugged into other chat clients that already offer accounts, history
and sharing. If a future deployment needs those features in this
gateway, that is the point at which adding storage would be worth its
extra weight.
