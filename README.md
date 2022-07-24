# avtodroch
#FTG module Droch bot



# meta developer: @Zekus

# scope: hikka_only

from .. import loader, utils
from asyncio import sleep


class DrochBotMod(loader.Module):
    """Рекомендуется делать это в лс бота либо же создать отдельную группу чтобы не мешать другим"""

    strings = {"name": "DrochBot"}

    async def drochcmd(self, message):
        """Включается комманда "/drochnut".Чтобы остановить, используйте  "Дрочка стоп"."""
        self.set("droch", True)
        while self.get("droch"):
            await message.reply("/drochnut")
            await sleep(0.1)
            await utils.answer(
                message, "Следующая команда будет произведена через 1 час и 5 минут."
            )
            await sleep(3960)

    async def dickcmd(self, message):
        """Включается комманда "/drochnut".Чтобы остановить, используйте  "Хуй стоп"."""
        self.set("dick", True)
        while self.get("dick"):
            await message.reply("/dick")
            await sleep(0.1)
            await utils.answer(
                message, "Следующая команда будет произведена через 6 часов."
            )
            await sleep(21600)

    async def casecmd(self, message):
        """Включается комманда "/case".Чтобы остановить, используйте  "кейс стоп"."""
        self.set("case", True)
        while self.get("case"):
            await message.reply("/case")
            await sleep(0.1)
            await utils.answer(
                message, "Следующая команда будет произведена через 24 часa."
            )
            await sleep(86400)

    async def watcher(self, message):
        if not getattr(message, "out", False):
            return

        if message.raw_text.lower() == "дрочка стоп":
            self.set("droch", False)
            await utils.answer(message, "<b>Дрочка остановлена.</b>")
        if message.raw_text.lower() == "хуй стоп":
            self.set("dick", False)
            await utils.answer(message, "<b>Рост хуя остановлен.</b>")
        if message.raw_text.lower() == "кейс стоп":
            self.set("case", False)
            await utils.answer(message, "<b>Открытие кейсов остановлено<b>")
