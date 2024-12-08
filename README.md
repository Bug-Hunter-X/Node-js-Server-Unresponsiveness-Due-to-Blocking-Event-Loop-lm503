# Node.js Server Unresponsiveness Due to Blocking Event Loop

This repository demonstrates a common Node.js issue: a server becoming unresponsive due to a long-running operation blocking the event loop.  The `bug.js` file showcases a server that hangs when processing a request that takes longer than expected.  The `bugSolution.js` demonstrates how to resolve this by using asynchronous operations to avoid blocking the event loop.

## Problem

Node.js is single-threaded, meaning that all operations run on a single thread – the event loop.  If a long-running operation is performed synchronously, it blocks this thread and prevents other requests from being processed, rendering the server unresponsive. This is often seen when handling large files, database interactions, or network requests without proper asynchronous handling. 

## Solution

To solve this, asynchronous operations like promises or async/await should be used. By offloading long tasks to a different thread or process, the event loop remains free to handle other requests, maintaining responsiveness.

## How to Run

1. Clone this repository.
2. Navigate to the directory.
3. Run the buggy server using: `node bug.js`  You'll observe that the server hangs, and requests will not be processed.
4. Run the fixed server using: `node bugSolution.js`.  This version processes requests concurrently, avoiding the blocking issue.

