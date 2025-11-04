# Week 9 - MCP Servers

You could spend a very long time tinkering MCP Servers, learning the full capabilities of the protocol, and ultimately do very cool things with them. But for this one-hour assignment, your task is only to set up one custom MCP server and possibly GitHub's MCP Server.

## Get this sample MCP server working with the SDK

1. Install the MCP Python SDK: `pip install "mcp\[cli]"`.
2. There is a sample Remote MCP Server in this folder. Get it working with `mcp dev`.

   1. I found my mcp.exe in my AppData Python folder here: `c:\\Users\\hays\\AppData\\Local\\Programs\\Python\\Python311\\Scripts\\mcp.exe`.
   2. With that on your PATH, start a new VS Code window and load the sample code from this folder.
   3. Open the Python code, `mcpserver.py`. Put a breakpoint on `return a + b` and run it in the Debugger.
   4. Now make a *second* Terminal in VS Code. You should be able run `mcp.exe dev ./mcpserver.py` and the browser should automatically open a generic page for testing MCP servers.
   5. The browser will have a box on the left for you to enter the URL to the MCP Server. The URL you need to enter is `http://localhost:8080/mcp`.
   6. Select Tools -> List Tools to load the tools from the MCP server.
   7. Below the Clear button, `thing\_a\_ma\_bobs` should show up as the only tool installed. (you might need to *scroll*). Click it, and a form will open that lets you test the call to the MCP Server.
   8. Enter a=2 and b=3, *scroll down*, then click Run Tool.
   9. Your VS Code should start flashing at you from the Task Bar. It should be stopped on the breakpoint that you set.
   10. Press Continue in VS Code to finish executing.
   11. Go back to the browser. Below the Run Tool button, there will now be a Tool Result: Success, with the Structured Content `{ result: 5 }`.

3. Modify the sample code now to do **subtraction** instead of addition.

   * For the same query above, you should get `{ result: -1 }` back.

4. Now let's integrate this MCP Server with your IDE's Agent Mode, per the demo in class.

   * Read about how to load MCP Servers into VS Code: https://code.visualstudio.com/docs/copilot/customization/mcp-servers
   * Other tips for developing MCP Servers for VS Code: https://code.visualstudio.com/api/extension-guides/ai/mcp
   * When you get it working, you should be able to open an empty text file in your IDE and prompt your Agent, "Thing a ma bobs 2 and 3". With minimal help from a static prompt in an Instructions/Memories file, the LLM should know exactly what you mean by that, the Agent should ask for permission to run the MCP server, and then it should return -1 (since we change the implementation above from addition to subtraction).

5. **Reflection:** In a new text document named `reflections.md`, answer the following questions:

   1. Why do you think we have MCP Servers? Why not just make Command Line Tools for Agents to run?
   2. What part of the sample MCP server makes the tool `thing_a_ma_bobs` appear in the list of tools? Why doesn't greet_user() appear as a tool?
   3. What part of the sample MCP server makes the parameters a and b appear, as number spinners at that, in the `mcp dev` web UI? How does `mcp dev` know that there are two integer parameters?


## Optional: Explore GitHub MCP Server

1. Get your IDE working with GitHub's MCP Remote Server: https://github.com/github/github-mcp-server/blob/main/docs/remote-server.md.

   * It wants you to configure a [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) on GitHub's web site with access to a personal repo of your choice.

2. Open that personal project in VS Code, and connect the GitHub MCP Server to it.
3. Ask the Agent to create an Issue for you, titled, "Publish My Work on Agent Mode and MCP Server capabilities", in that project. It should indeed create said Issue on your personal GitHub project without any fuss.
4. **Reflection:** Answer the following questions:

    1. Why do you think this GitHub MCP Server exists? What problem are they trying to solve?
    2. Do you think you would benefit from using GitHub's MCP Server in your professional work? Why or why not?
    3. If you were assigned to implement your own GitHub MCP Server that can create Issues, how would you implement the ability to create Issues? (hint: your code would need the user's Personal Access Token)

## Submission instructions

Turn in a .zip file of your project with reflections.md to Moodle.
