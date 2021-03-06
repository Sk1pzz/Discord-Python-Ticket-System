[![Discord Bots](https://top.gg/api/widget/status/739740219544305714.svg)](https://top.gg/bot/739740219544305714)

# Ticket-Bot
A discord ticket system with PostgreSQL.

# Information
This is not supposed to be a copy and paste exercise, if you want to recreate the system, learn python first. 

If you have any improvement suggestions feel free to contact me.

### NOT for beginners of discord.py!

If you are completly new to discord.py or generally python - DO NOT JUST copy the code - study the syntax first and try slightly easier projects. 

# Requirements

- Python 3.8.6 or higher
- discord.py (Tested with version 1.6.0)
- PostgreSQL Database (I am using a local PostgreSQL Database)
- asyncpg

# How to create a local PostgreSQL Database

1. Download the installer from the [website](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).

2. After the download is complete start the installation by double-clicking on the .exe. 

3. A Setup-Window should show up. Just keep clicking on NEXT until the [password window](https://cdn.discordapp.com/attachments/771635939700768769/827816815886991380/unknown.png). 

4. **Choose a good and secure password and remember it!** 

5. You can use the default settings for the next two windows.

6. Now start the [installation](https://cdn.discordapp.com/attachments/771635939700768769/827819917829996554/unknown.png).

7. After the installation is finished you shuold see this [window](https://cdn.discordapp.com/attachments/771635939700768769/827813661182525460/unknown.png). You dont need to launch Stack-Builder - just click on finish. 

8. Open the PostgreSQL folder and click on [pgAdmin4](https://cdn.discordapp.com/attachments/771635939700768769/827823887495856128/unknown.png).

9. After pgAdmin4 has loaded, it will ask you for the [password](https://cdn.discordapp.com/attachments/771635939700768769/827824348562849802/unknown.png) you chose during the installation.

10. Click on **Servers** on the left side and open **Databases**. You can see that one database with the name **postgres** already exists. 

11. Right-Click on Databases and select **Create Database**. Name it **PostgreSQL-Tickets** and click on save.

12. The Database should appear on the left side. Open it and scroll down to **Schemas**. You can find **Tables** directly below. 

13. Right-Click on Tables and create a new one. Call it **tickets** and add two columns named ``guild_id`` and ``ticket_id``. Like [this](https://cdn.discordapp.com/attachments/771635939700768769/845238042768048138/unknown.png).

14. Add a second table named **requests**. Add four columns with the names: ``guild_id``, ``channel_name``, ``channel_id`` and ``user_id``. Like [this](https://cdn.discordapp.com/attachments/771635939700768769/840122943220088852/unknown.png).

15. Dont close pgAdmin4 yet, you will need it later again.

# How to create the same bot for your server
1. Go on the [discord developer portal](https://discord.com/developers/applications) and make a new application. Now create a new bot and add him to your server.

2. Open ``data.json`` and fill in your bot-token and db-password (*The one you created at the beginning*)

3. Start the bot and type ``?ticket`` in your ticket-channel. A [message](https://cdn.discordapp.com/attachments/771635939700768769/827460503185653790/unknown.png) should show up.

4. Open the database again and fill in the missing two IDs.

4.1. Right-Click on ``tickets`` and click on ``View / Edit Data`` -> ``All Rows``.

4.2. Double-Click in the [empty spaces](https://cdn.discordapp.com/attachments/771635939700768769/845239738273366036/unknown.png) and fill in the ID of your ticket-message and the ID of your guild.

4.3. After you filled in both IDs save them by clicking on the [little arrow](https://cdn.discordapp.com/attachments/771635939700768769/845240257602781224/unknown.png)

5. When you are done, restart the bot and click on the 📩. You should see a new channel with a [message](https://cdn.discordapp.com/attachments/771635939700768769/840124556731088896/unknown.png) inside.

#### If you want to change the embed-message open ``ticket.py``.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
```python
@commands.command()
@commands.has_permissions(administrator=True)
async def ticket(self, ctx):

    embed = discord.Embed(
        title="Would you like to create a ticket?", 
        description="If you have any questions or concerns create a new ticket by clicking on the emoji below this message.", 
        color=0xf7fcfd)

    embed.add_field(name="Do you want to report someone?", value="Please contact a supporter or moderator directly!", inline=True)
    embed.set_thumbnail(url="https://cdn.discordapp.com/attachments/771635939700768769/773121323341578250/external-content.duckduckgo.com.png")
    embed.set_author(name="TiLiKas-Tickets")

    msg = await ctx.send(embed=embed)
    await msg.add_reaction("📩")
```
**I would recommend to change the authors-name (TiLiKas-Tickets)**

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

There are three options for the message in the ticket channel.

✅ -> Claim the ticket (*The creator of the ticket cant claim it*)

📌 -> Mention every supporter (*Does not do anything right now - I'm at it!*)

🔒 -> Close the ticket - the channel will be delete after 10 seconds.

After clicking on the lock, the channel will be deleted and a new channel named **ticket-log** will appear.
# Done

If you did everything correctly your bot should work like in the examples!

Still questions? Join my [discord server](https://discord.gg/ykF6UfqWgF).

I am not going to explain how it works with other databases! (Or Replit)

**As I wrote at the beginning, this tutorial is not for beginners!**

