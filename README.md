# ISOBEL 🐶

Welcome!

Isobel is a beginner friendly server framework for fetching data from your social profiles and other sources, for display in your own apps and websites.

Isobel periodically fetches data from the services that you teach her, so the data is always there when you need it. A great example is Twitter, which gets the latest posts from your Twitter feed. Once configured, you can access the JSON for your latest tweets at a defined URL, so you can display them on your website. That means no worrying about API rate-limiting or quotas, and no making API calls from your frontend (a big no-no).

Isobel includes a bunch of premade services, but you can also create your own.

Here is a minumum implementation of Isobel.

```javascript
const ISOBEL = require("@isobel/core");
const fileSystem = require("@isobel/file-system");
const nasa = require("@isobel/nasa");

// initialise
const Isobel = new ISOBEL({
  cache: fileSystem,
  endpoints: [
    {
      name: "nasa",
      func: nasa.fetchPhotoOfTheDay, // gets the NASA photo of the day
      interval: 24 * 60 * 60 * 1000; // every 24 hours
    }
  ]
});

Isobel.start().catch(error => {
  console.error("Error:", error);
  process.exit(1);
});
```
