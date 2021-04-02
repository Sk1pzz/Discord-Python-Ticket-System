# Ticket-Bot
A discord ticket system with PostgresQL

# Information
This is not supposed to be a copy and paste exercise, if you want to recreate the system, learn the python basics first. 

If you have any improvement suggestions feel free to contact me.

### For beginners of discord.py!

If you are completly new to discord.py or generally python - DO NOT JUST copy the code - study the syntax first and try slightly easier projects. 

# Requirements

- Python 3.8.6 ([download](https://www.python.org/downloads/release/python-386/))
- discord.py (pip install -U discord.py[voice]) (Tested with version 1.6.0)
- PostgresSQL Database (https://www.postgresql.org/download/) (or anything similar)
- pip install asyncpg

# How to create the same bot for your server
1. Go on the [discord developer portal](https://discord.com/developers/applications) and make a new application. Now create a new bot and add him to your server.

2. Create a database named ``PostgresSQL-Tickets`` and add two tables.  

3. Name the first table ``tickets`` and the second one ``requests``. 

4. Add two columns (guild_id and ticket_id) to the [tickets-table](https://cdn.discordapp.com/attachments/771635939700768769/827459057223860254/unknown.png). Make sure that ``guild_id`` is a primary key.

5. Add three columns (guild_id, channel_name and channel_id) to the [requests-table](https://cdn.discordapp.com/attachments/771635939700768769/827459186870190100/unknown.png). **We do not need a primary key here!**

6. Start the bot and type ``?ticket`` in your ticket-channel. A message [like](https://cdn.discordapp.com/attachments/771635939700768769/827460503185653790/unknown.png) this should pop up.

7. Now copy the ID of your server and the message you just created and fill it in the database. Your DB should look like [this](https://cdn.discordapp.com/attachments/771635939700768769/827460984628183060/unknown.png).

8. If you want to edit the embed-message open ``ticket.py``.

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
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

You can change the text of the embed however you want - **change the author-name (TiLiKas-Tickets)**

9. If you now restart the bot and click on the 📩 a new channel with a [message](https://cdn.discordapp.com/attachments/771635939700768769/827462375803191326/unknown.png) should appear.



---------------------------------------------------------------------------------------------------------------------------------------------------------------------
```python

```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

**ALSO dont forget to change the authors name to the name of your bot!**

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

You have three diffrent emoji choices:

✅ -> Claim the ticket ([example](https://cdn.discordapp.com/attachments/771635939700768769/798489702093029376/unknown.png)) (*The creator of the ticket cant claim it*)

⛔ -> Mention every supporter ([example](https://cdn.discordapp.com/attachments/771635939700768769/798487939063087133/unknown.png))

🔒 -> Close the ticket - channel will delete itself after 10 seconds ([example](https://cdn.discordapp.com/attachments/771635939700768769/798488068038328330/unknown.png))

**After closing the ticket it will no longer be accessable**

# Done

If you did everything correctly the bot should work like in the examples!

Still questions? Join my [discord server](https://discord.gg/WRH22qat76)

(I will not reply to E-Mails)
