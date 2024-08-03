# RobloxStudio
//Tum kodlar asagida yer almaktadir.
Coin Scriptine ait kod aşağıdadır.
local part=script.Parent
part.Touched:Connect(function(hit)
	local character=hit.Parent
	local humanoid=character:FindFirstChildOfClass("Humanoid")
local player= game.Players:GetPlayerFromCharacter(character)
if player then
	local leaderstats=player:FindFirstChild("leaderstats")
	if leaderstats then
		local coins=leaderstats:FindFirstChild("Coins")
		if coins then
			coins.Value=coins.Value+10
			part:Destroy()
			
		end
	end
	end
	part.Transparency=1
	part.CanCollide=false
	wait(5)
	part.Transparency=0
	part.CanCollide=true
	part:Destroy()
	debounce=false
end	
end)


//LiderTablosuna ait kod asagidadir
game.Players.PlayerAdded:Connect(function(player)
	local leaderstats=Instance.new("Folder")
	leaderstats.Name="leaderstats"
	leaderstats.Parent=player
	local coins=Instance.new("IntValue")
	coins.Name="Coins"
	coins.Value=0
	coins.Parent=leaderstats
end)
//Blogun Rengarenk Olmasini Saglayan Kod asagidadir.
local part=script.Parent
while true do
	local randomColor=Color3.fromRGB(math.random(0,255), math.random(0,255), math.random(0,255))
	part.Color=randomColor
	wait(1)
end
//Asansorun Kodu
local TweenService = game:GetService("TweenService")

local block = script.Parent
local moveDistance = 20
local moveTime = 2

local startPosition = block.Position

local tweenInfo = TweenInfo.new(
	moveTime, 
	Enum.EasingStyle.Quad, 
	Enum.EasingDirection.Out
)

local function moveBlock()

	local upPosition = startPosition + Vector3.new(0, moveDistance, 0)
	local upTween = TweenService:Create(block, tweenInfo, {Position = upPosition})

	local downPosition = startPosition - Vector3.new(0, moveDistance, 0)
	local downTween = TweenService:Create(block, tweenInfo, {Position = downPosition})

	upTween:Play()
	upTween.Completed:Wait() 

	downTween:Play()
	downTween.Completed:Wait()


	local startTween = TweenService:Create(block, tweenInfo, {Position = startPosition})
	startTween:Play()
	startTween.Completed:Wait() 
end


while true do
	moveBlock()
	wait(moveTime * 2) 
end

//Kapı acma kapamanın kodu asagidadir
local clickDetector = script.Parent:FindFirstChild("ClickDetector")

local Kapi = game.Workspace:FindFirstChild("KapıPart")

local function AçKapı()
	if Kapi then
		Kapi.Transparency = 0.5
		Kapi.CanCollide = false
		wait(5)
		Kapi.Transparency = 0
		Kapi.CanCollide = true
	else
		warn("Kapı bulunamadı!")
	end
end

if clickDetector then
	clickDetector.MouseClick:Connect(AçKapi)
else
	warn("ClickDetector bulunamadı!")
end
// ve kapinin kodu
local kapıModel = game.Workspace:FindFirstChild("KapıModel")

local function AçKapı()
	if kapModel then
		for _, parça in pairs(kapıModel:GetChildren()) do
			if parça:IsA("Part") then
				parça.Transparency = 0.5
				parça.CanCollide = false
			end
		end
		wait(5)
		for _, parça in pairs(kapıModel:GetChildren()) do
			if parça:IsA("Part") then
				parça.Transparency = 0
				parça.CanCollide = true
			end
		end
	else
		warn("Kapı modeli bulunamadı!")
	end
end

if clickDetector then
	clickDetector.MouseClick:Connect(AçKapı)
else
	warn("ClickDetector bulunamadı!")
end
//oldurmeKodu
local blok = script.Parent
blok.Anchored = true

function oldurmeKodu(hit)
	local karakter=hit.Parent
	local humanoid=karakter:FindFirstChildOfClass("Humanoid")
	if humanoid then
		humanoid.Health = 0
	end

end

blok.Touched:Connect(oldurmeKodu)
