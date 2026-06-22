Скачать dnSpy ( https://github.com/dnSpy/dnSpy )

Откройте dnSpy, Файл -> Открыть -> Перейдите в эту папку внутри вашей установки Bannerlord
: C:\Program Files (x86)\Steam\steamapps\common\Mount & Blade II Bannerlord\bin\Win64_Shipping_Client

Откройте файл TaleWorlds.CampaignSystem.dll

В dnSpy перейдите в меню «Редактировать» -> «Поиск сборок» -> введите «GetPlayerMapMovementSpeedBonusMultiplier» (без кавычек).

Дважды щелкните по второму файлу — то есть по тому, у которого в названии присутствует "TaleWorlds.CampaignSystem.GameComponents.Default DifficultyModel " (у другого файла нет слова "Default").
// TaleWorlds.CampaignSystem.GameComponents.DefaultDifficultyModel
// Token: 0x06001A87 RID: 6791 RVA: 0x000A1454 File Offset: 0x0009F654
public override float GetPlayerMapMovementSpeedBonusMultiplier()
{
	switch (CampaignOptions.PlayerMapMovementSpeed)
	{
	case CampaignOptions.Difficulty.VeryEasy:
		return 0.1f;
	case CampaignOptions.Difficulty.Easy:
		return 0.05f;
	case CampaignOptions.Difficulty.Realistic:
		return 0f;
	default:
		return 0.1f;
	}
}**

**

Теперь вы увидите параметры «Очень легко», «Легко» и «Реалистично», а также соответствующие возвращаемые значения, например, «return 0.05f». Это число показывает, какой процент множителя скорости добавляется к вашей группе при выборе режима сложности «Скорость группы» в игре. Если вы играете на уровне сложности «Реалистично» для скорости группы, вам нужно изменить значение «CampaignOptions.Difficulty.Realistic», если вы играете на уровне «Легко», то вам нужно изменить значение, заканчивающееся на «.Easy». НЕ МЕНЯЙТЕ ЗНАЧЕНИЕ ЗДЕСЬ.

Щелкните правой кнопкой мыши по полю "return XYZ" в нужном вам варианте сложности и выберите "Редактировать инструкции IL". Вы увидите другое окно с теми же процентными значениями (без буквы "f" после них). Значение, которое вы хотите изменить, будет выделено. Если вы хотите, чтобы ваш бонус увеличивал скорость группы на 20%, измените значение на "0,2" (это запятая, а не десятичная точка), если вы хотите увеличить скорость на 50%, введите "0,5" и так далее.

Нажмите ОК — если вы изменили скорость на 20%, значение сложности теперь должно отображаться как "return 0,2f;".

Перейдите в меню «Файл» — «Сохранить все».

Готово — если в настройках "Скорость группы" указан только что измененный уровень сложности, скорость вашей группы должна измениться соответствующим образом.
