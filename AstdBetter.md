
        game.Players.LocalPlayer.Idled:Connect(function()
            game:GetService("VirtualUser"):CaptureController()
            game:GetService("VirtualUser"):ClickButton2(Vector2.new())
        end)


local TeleportCheck = false
local queueteleport = (syn and syn.queue_on_teleport) or queue_on_teleport or (fluxus and fluxus.queue_on_teleport)
game.Players.LocalPlayer.OnTeleport:Connect(function(State)
    if (not TeleportCheck) and queueteleport then
        TeleportCheck = true
        queueteleport("loadstring(game:HttpGet('https://raw.githubusercontent.com/Xisuno/Test/refs/heads/main/README.md'))()")
    end
end)

local items = {"Trait","Orb","Pure"}

local sold = {}

function getWave()
   local String = game:GetService("Players").LocalPlayer.PlayerGui.GU.MenuFrame.TopFrame.InfoFrame:WaitForChild("Wave").Title.Text
   local Wave = string.gsub(String, "/15", "")
   return tonumber(Wave)
end


-- função spawn
function spawn(name, cf, maxup)

if table.find(sold,name) then return end




    local max
    if maxup == nil then
        max = 999
    else
        max = maxup
    end

    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SetEvent"):FireServer(
        "GameStuff",
        {
            "Summon",
            name,
            cf
        }
    )

    for i, v in workspace.UnitFolder:GetChildren() do
        if v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position - cf.Position).Magnitude < 1 then
            v:SetAttribute("MaxUpF", max)
        end
    end
end

function setup(world)

-----------------------------------------------------------------------
    if world == "naruto" then
        local farmup = 0
        task.spawn(function()
            while task.wait(0.1) do

                if #workspace.UnitFolder:GetChildren() == 0 or #workspace.UnitFolder:GetChildren() >= 4 then
                    farmup = 999
                else
                    farmup = 0
                end

spawn("Teiuchi", CFrame.new(119.4036636352539, 55.58282470703125, 55.2382926940918, 1, 0, 0, 0, 1, 0, 0, 0, 1),farmup)
spawn("Ulquiorra", CFrame.new(100.7954330444336, 61.46331787109375, 40.51166534423828, 1, 0, 0, 0, 1, 0, 0, 0, 1),5)

                if workspace.UnitFolder:FindFirstChild("Ulquiorra") and workspace.UnitFolder.Ulquiorra:GetAttribute("UpgradeLevel") >= 2 then
spawn("Gray", CFrame.new(120.38383483886719, 55.58282470703125, 43.427894592285156, 1, 0, 0, 0, 1, 0, 0, 0, 1))
spawn("Kokushibo", CFrame.new(113.9775619506836, 55.58282470703125, 41.76774978637695, 1, 0, 0, 0, 1, 0, 0, 0, 1))
                end


            end
        end)
------------------------------------------------------------------------
    elseif world == "innovation" then
        local farmup = 0
        task.spawn(function()
            while task.wait(0.1) do

                if #workspace.UnitFolder:GetChildren() == 0 or #workspace.UnitFolder:GetChildren() >= 3 then
                    farmup = 999
                else
                    farmup = 0
                end


spawn("Teiuchi", CFrame.new(-61.23674392700195, 3.7593679428100586, -11.362281799316406, 1, 0, 0, 0, 1, 0, 0, 0, 1),farmup)
spawn("Ulquiorra", CFrame.new(-137.02146911621094, 9.920669555664062, -68.43455505371094))

                if workspace.UnitFolder:FindFirstChild("Ulquiorra") and workspace.UnitFolder.Ulquiorra:GetAttribute("UpgradeLevel") >= 2 then
spawn("Gray", CFrame.new(-94.13842010498047, 3.7593679428100586, -76.62786865234375))
                end

            end
        end)
--------------------------------------------------------
    elseif world == "bleach" then
        local farmup = 0
        task.spawn(function()
            while task.wait(0.1) do

                if #workspace.UnitFolder:GetChildren() == 0 or #workspace.UnitFolder:GetChildren() >= 4 then
                    farmup = 999
                else
                    farmup = 0
                end

spawn("Teiuchi", CFrame.new(58.710575103759766, 48.47781753540039, -13.824424743652344),farmup)
spawn("Ulquiorra", CFrame.new(138.03330993652344, 59.550113677978516, -44.54417419433594))

                if workspace.UnitFolder:FindFirstChild("Ulquiorra") and workspace.UnitFolder.Ulquiorra:GetAttribute("UpgradeLevel") >= 2 then
spawn("Kokushibo", CFrame.new(123.972412109375, 48.47781753540039, -91.41800689697266))
spawn("Sukuna", CFrame.new(152.96690368652344, 51.84920120239258, -91.12712097167969))
                end


            end
        end)
-------------------------------------------------------
    elseif world == "aot" then
        local farmup = 0
        task.spawn(function()
            while task.wait(0.1) do

                if #workspace.UnitFolder:GetChildren() == 0 or #workspace.UnitFolder:GetChildren() >= 3 then
                    farmup = 999
                else
                    farmup = 0
                end

spawn("Teiuchi", CFrame.new(17.817543029785156, 1.526009202003479, -689.9090576171875, 1, 0, 0, 0, 1, 0, 0, 0, 1),farmup)
spawn("Sukuna", CFrame.new(30.07181739807129, 3.951678514480591, -730.4588623046875, 1, 0, 0, 0, 1, 0, 0, 0, 1),4)

                if workspace.UnitFolder:FindFirstChild("Sukuna") and workspace.UnitFolder.Sukuna:GetAttribute("UpgradeLevel") >= 2 then
spawn("Kokushibo", CFrame.new(28.962060928344727, 1.526009202003479, -753.997314453125, 1, 0, 0, 0, 1, 0, 0, 0, 1),3)
spawn("Esdeath", CFrame.new(44.9014778137207, 1.526009202003479, -732.4254760742188, 1, 0, 0, 0, 1, 0, 0, 0, 1))
                end
                if getWave() >= 15 then
task.wait(24)
if workspace.UnitFolder:FindFirstChild("Esdeath") then
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(    {
        Type = "GameStuff"
    },
    {
        "SpecialMove",
        workspace.UnitFolder.Esdeath,
        "SpecialMove",
        "UseAbility"
    })
                  end
               end
            end
        end)
----------------------------------------------------
    elseif world == "dragonball" then
        local farmup = 0
        task.spawn(function()
            while task.wait(0.1) do

                if #workspace.UnitFolder:GetChildren() == 0 or #workspace.UnitFolder:GetChildren() > 1 then
                    farmup = 999
                else
                    farmup = 0
                end


                spawn("Teiuchi", CFrame.new(-266.0371398925781, 424.6287536621094, -152.15606689453125),farmup)
                spawn("Ulquiorra", CFrame.new(-220.30996704101562, 427.58001708984375, -79.07366943359375))

                if workspace.UnitFolder:FindFirstChild("Ulquiorra") and workspace.UnitFolder.Ulquiorra:GetAttribute("UpgradeLevel") >= 2 then
                spawn("Sukuna", CFrame.new(-216.07650756835938, 427.636962890625, -79.61184692382812),4)
                spawn("Kokushibo", CFrame.new(-209.5087127685547, 424.6271057128906, -71.33582305908203, 1, 0, 0, 0, 1, 0, 0, 0, 1),3)
                end
                
                task.spawn(function()
                if getWave() >= 15 then
                game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(	{
		Type = "GameStuff"
	},
	{
		"Priority",
		workspace:WaitForChild("UnitFolder")["Sukuna"],
		false,
		true
	})
                     end
                end)


            end
        end)
----------------------------------------------------------------


    end

--------------------final
end

workspace:WaitForChild("Map"):WaitForChild("Buildings",10)

if workspace:WaitForChild("Map"):FindFirstChild("Buildings") then

game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("MainUI"):WaitForChild("WorldFrame")
game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui", 999):WaitForChild("MainUI", 999) :WaitForChild("WorldFrame", 999):WaitForChild("WorldFrame", 999):WaitForChild("MainFrame", 999):WaitForChild("StageFrame", 999):WaitForChild("Stages", 999):WaitForChild("StageScroll", 999):WaitForChild("Challenge5", 999)
game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui", 999):WaitForChild("MainUI", 999):WaitForChild("ResultFrame", 999):WaitForChild("Result", 999):WaitForChild("ExpandFrame", 999):WaitForChild("ButtonFrame", 999):WaitForChild("ButtonExpand", 999):WaitForChild("Return", 999)

for i = 1,50 do
firesignal(game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.FadeFrame.Activated)
firesignal(game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.Result.ExpandFrame.ButtonFrame.ButtonExpand.Return.Activated)
task.wait(0.1)
end

local chall = {
{},
{},
{},
{},
{}
}

local diff = "Hard"

for number = 1, 5 do 
if not game:GetService("Players").LocalPlayer.PlayerGui.MainUI.WorldFrame.WorldFrame.MainFrame.StageFrame.Stages.StageScroll["Challenge"..tostring(number)]:FindFirstChild("ExpandFrame") then break end
table.insert(chall[number],game:GetService("Players").LocalPlayer.PlayerGui.MainUI.WorldFrame.WorldFrame.MainFrame.StageFrame.Stages.StageScroll["Challenge"..tostring(number)].ExpandFrame.InnerFrame.CanvasGroup.LText.Text)
    for _,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.MainUI.WorldFrame.WorldFrame.MainFrame.StageFrame.Stages.StageScroll["Challenge"..tostring(number)]:GetDescendants()) do
        if v:IsA("ImageButton") or v:IsA("TextButton") then
            firesignal(v.Activated)
task.wait(0.1)

firesignal(game:GetService("Players").LocalPlayer.PlayerGui.MainUI.WorldFrame.WorldFrame.MainFrame.RightFrame.InfoFrame.InfoInner.BoxFrame.InfoFrame2.InnerFrame.RecordFrame.RecordInfo.DifficultFrame[diff].Button.Activated)

            task.wait(0.1)

            for i,v in game:GetService("Players").LocalPlayer.PlayerGui.MainUI.WorldFrame.WorldFrame.MainFrame.RightFrame.InfoFrame.InfoInner.BoxFrame.InfoFrame2.InnerFrame.CanvasFrame.CanvasGroup.BottomFrame.DetailFrame.RewardFrame.Rewards.RewardScroll:GetChildren() do
                if v.Name == "ItemFrame2" then
                    table.insert(chall[number], v.ExpandFrame.ClickFrame.HoverFrame.BlackInner.DisplayFrame.NamePriceFrame:GetChildren()[1].Text)
                end
            end

            task.wait()
        end
    end
end

repeat task.wait() until chall[4][1] ~= nil

task.wait(0.5)

local found = false

for number = 1, #items do 
	for challn = 1, 5 do
		for i, v in ipairs(chall[challn]) do
			if string.match(v, items[number]) and not table.find(chall[challn], "Random Units") and not table.find(chall[challn], "High Cost") then
                        if found then break end
                        found = challn
				
				repeat task.wait(1)
					for _, pod in ipairs(workspace:WaitForChild("Map").Buildings.ChallengePods:GetChildren()) do
						if pod.Name == "Pod" and pod.Root.SurfaceGui.Frame.WaitFrame.TimeText.Text == "" then
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = pod.PrimaryPart.CFrame
							game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
							task.wait()
							game:GetService("VirtualInputManager"):SendKeyEvent(false, "E", false, game)
						end
					end
				until game:GetService("Players").LocalPlayer.PlayerGui.MainUI.WorldFrame.WorldFrame.Visible == true
				
			end
		end
	end
end

task.spawn(function()
	while true do task.wait(0.1)
		if found then
			for challstage = 1,6 do
				game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer({
					Chapter = challstage,
					Type = "Lobby",
					Name = "Challenge"..tostring(found),
					Difficulty = "Hard",
					Mode = "Pod",
					Friend = false,
					Update = true
				})
			end
			game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer({
				Start = true,
				Type = "Lobby",
				Update = true,
				Mode = "Pod"
			})
		end
	end
end)


--setup

elseif not workspace:WaitForChild("Map"):FindFirstChild("Buildings") then

task.wait(5)

game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("GU"):WaitForChild("MenuFrame")
game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("GU"):WaitForChild("MenuFrame"):WaitForChild("TopFrame"):WaitForChild("InfoFrame"):WaitForChild("Wave")

task.spawn(function()

while task.wait(0.2) do

task.spawn(function()

if getWave() <= 5 then
sold = {}
end

if getWave() >= 15  and workspace.UnitFolder:FindFirstChild("Teiuchi") then

table.insert(sold,"Teiuchi")
task.wait(5)
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(	{
		Type = "GameStuff"
	},
	{
		"Sell",
		workspace.UnitFolder.Teiuchi
	})

     end
 end)


if game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.Result.ExpandFrame.ButtonFrame.ButtonExpand.Replay:FindFirstChild("ButtonDesign") and game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.Result.ExpandFrame.ButtonFrame.ButtonExpand.Replay.ButtonDesign.ExpandFrame.DisabledFrame.Visible == true then
firesignal(game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.Result.ExpandFrame.ButtonFrame.ButtonExpand.Return.Activated)
elseif game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.Result.ExpandFrame.ButtonFrame.ButtonExpand.Replay:FindFirstChild("ButtonDesign") and game:GetService("Players").LocalPlayer.PlayerGui.MainUI.ResultFrame.Result.ExpandFrame.ButtonFrame.ButtonExpand.Replay.ButtonDesign.ExpandFrame.DisabledFrame.Visible == false then
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(	{
		Type = "Map",
		Mode = "Get"
	})

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(	{
		Type = "Game",
		Index = "Replay",
		Mode = "Reward"
	})

end

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GameStuff"):FireServer("SkipVoteYes")

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(	{
		Index = 2,
		Type = "Speed"
	})

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GameStuff"):FireServer("StartVoteYes")

for i,v in workspace.UnitFolder:GetChildren() do

if v:GetAttribute("MaxUpF") ~= 0 and v:GetAttribute("MaxUpF") ~= v:GetAttribute("UpgradeLevel") then
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(	{
	Type = "GameStuff"
	},
	{
		"Upgrade",
		v
	})
end

if v.Name ~= "Esdeath" then
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("GetFunction"):InvokeServer(    {
        Type = "GameStuff"
    },
    {
        "SpecialMove",
        v,
        "SpecialMove",
        "UseAbility"
    })
end

end

end

end)

end

if workspace:FindFirstChild("Portal") and workspace:FindFirstChild("Portal"):FindFirstChild("Stairs_StairTex") then

setup("naruto")

elseif workspace:FindFirstChild("Don't Care") and workspace["Don't Care"]:FindFirstChild("Map") and workspace["Don't Care"].Map.Buildings.EggHead_Rocket ~= nil then

setup("innovation")

elseif workspace:FindFirstChild("Dont Care") and workspace["Dont Care"]:FindFirstChild("Arch") ~= nil then

setup("bleach")

elseif workspace:FindFirstChild("Don't Care") and workspace["Don't Care"].Vfx:FindFirstChild("LampV2") then

setup("dragonball")

elseif workspace:FindFirstChild("Red portal") then

setup("aot")

end

local waitt = 50

if not workspace:WaitForChild("Map"):FindFirstChild("Buildings") then
waitt = 2350
elseif workspace:WaitForChild("Map"):FindFirstChild("Buildings") then
waitt = 50
end

print(waitt)
task.wait(waitt)

while task.wait() do 
game:GetService("TeleportService"):Teleport(17687504411)
end
 
