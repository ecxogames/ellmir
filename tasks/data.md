## Task
- Rework the local storage structure of my app to follow a more efficient and organized approach.
- There must be just a few local storage keys that are objects storing more data depending on the type of data.
- For example, a key called `auth` could store an object with properties like `toke`, `uid`, and `expiry`. Another key called `settings` could store an object with properties like `theme`, `language`, or other properties containing objects, arrays, strings, etc.
- In case where a data wants to be stored on the local storage, there must be a `dump` key where all the things saved to local storage without specification will be falling back to. For example, if a data is saved to local storage without specifying a key, it will be stored in the `dump` key as if it was a key, then when getting the key (eg. localStorage.getItem('<key-name>')), it will check if the key exists, if not, check if the key exists in the `dump` key, and if it does, return the value from there. If it doesn't exist in either, return null.

## Input
This task should be refered in the prompt (eg. "Execute @data.md").

## Output
The action from this task is to rework the local storage structure of your app to follow a more efficient and organized approach. The output will be a new local storage structure with fewer keys that store objects containing more data, as well as a `dump` key for fallback storage.