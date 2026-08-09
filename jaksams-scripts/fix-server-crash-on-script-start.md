---
title: "Fix server crash on script start"
description: "Resolve server crashes caused by an outdated mysql-async script"
---

If your server crashes when starting the script, it means you are using an old version of the `mysql-async` script.

Fixing this issue is very simple and fast, you have 2 options:

<CardGroup cols={2}>
  <Card title="Install OxMySQL" icon="database" href="https://overextended.github.io/docs/oxmysql/">
    **Strongly recommended.** Replaces `mysql-async` with improved performance and full compatibility, allowing an easy swap. Check the installation guide for details.
  </Card>

  <Card title="Update mysql-async" icon="download" href="https://github.com/brouznouf/fivem-mysql-async">
    **Not recommended.** Install the updated script instead of your current `mysql-async`. Be sure to rename the script folder to `mysql-async`.
  </Card>
</CardGroup>