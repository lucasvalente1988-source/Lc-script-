-- GUI Principal - Painel Leon
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local TitleLabel = Instance.new("TextLabel")
local LeoImage = Instance.new("ImageLabel")
local CreditLabel = Instance.new("TextLabel")
local ESPButton = Instance.new("TextButton")
local HealthButton = Instance.new("TextButton")
local AimCircleButton = Instance.new("TextButton")
local AimCircle = Instance.new("Frame")

-- Configurações
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.Name = "LeonPanel"
ScreenGui.ResetOnSpawn = false

-- Frame principal (painel branco)
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.new(1, 1, 1)
MainFrame.BackgroundTransparency = 0.1
MainFrame.BorderSizePixel = 0
MainFrame.Position = UDim2.new(0.02, 0, 0.1, 0)
MainFrame.Size = UDim2.new(0, 200, 0, 300)
MainFrame.Active = true
MainFrame.Draggable = true

-- Título "Leon script"
TitleLabel.Parent = MainFrame
TitleLabel.BackgroundTransparency = 1
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.Size = UDim2.new(1, 0, 0, 30)
TitleLabel.Text = "Leon script"
TitleLabel.TextColor3 = Color3.new(0, 0, 0)
TitleLabel.TextScaled = true
TitleLabel.Font = Enum.Font.GothamBold

-- Imagem do leão (usando um asset placeholder - substitua pelo ID da imagem desejada)
LeoImage.Parent = MainFrame
LeoImage.BackgroundTransparency = 1
LeoImage.Position = UDim2.new(0.25, 0, 0.12, 0)
LeoImage.Size = UDim2.new(0.5, 0, 0.3, 0)
LeoImage.Image = "rbxassetid://136587446" -- ID de um leão placeholder

-- Crédito "lucas"
CreditLabel.Parent = MainFrame
CreditLabel.BackgroundTransparency = 1
CreditLabel.Position = UDim2.new(0.7, 0, 0.9, 0)
CreditLabel.Size = UDim2.new(0.3, 0, 0.1, 0)
CreditLabel.Text = "lucas"
CreditLabel.TextColor3 = Color3.new(0, 0, 0)
CreditLabel.TextScaled = true
CreditLabel.Font = Enum.Font.SourceSans

-- Botão ESP
ESPButton.Parent = MainFrame
ESPButton.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
ESPButton.Position = UDim2.new(0.1, 0, 0.45, 0)
ESPButton.Size = UDim2.new(0.8, 0, 0.1, 0)
ESPButton.Text = "ESP"
ESPButton.TextColor3 = Color3.new(1, 1, 1)

-- Botão Vida
HealthButton.Parent = MainFrame
HealthButton.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
HealthButton.Position = UDim2.new(0.1, 0, 0.6, 0)
HealthButton.Size = UDim2.new(0.8, 0, 0.1, 0)
HealthButton.Text = "Vida"
HealthButton.TextColor3 = Color3.new(1, 1, 1)

-- Botão Aim Circle
AimCircleButton.Parent = MainFrame
AimCircleButton.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
AimCircleButton.Position = UDim2.new(0.1, 0, 0.75, 0)
AimCircleButton.Size = UDim2.new(0.8, 0, 0.1, 0)
AimCircleButton.Text = "Aim Circle"
AimCircleButton.TextColor3 = Color3.new(1, 1, 1)

-- Círculo de mira (invisível inicialmente)
AimCircle.Parent = ScreenGui
AimCircle.BackgroundTransparency = 0.5
AimCircle.BackgroundColor3 = Color3.new(1, 0, 0)
AimCircle.Size = UDim2.new(0, 100, 0, 100)
AimCircle.Position = UDim2.new(0.5, -50, 0.5, -50)
AimCircle.Visible = false
AimCircle.BorderSizePixel = 2
AimCircle.BorderColor3 = Color3.new(1, 1, 1)

-- Funções dos botões
ESPButton.MouseButton1Click:Connect(function()
    local players = game:GetService("Players")
    local localPlayer = players.LocalPlayer
    
    -- Mostra coordenadas dos jogadores no chat (apenas exemplo)
    for _, player in ipairs(players:GetPlayers()) do
        if player ~= localPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local pos = player.Character.HumanoidRootPart.Position
            game.StarterGui:SetCore("ChatMakeSystemMessage", {
                Text = string.format("%s está em: X=%.1f, Y=%.1f, Z=%.1f", player.Name, pos.X, pos.Y, pos.Z),
                Color = Color3.new(0, 1, 0)
            })
        end
    end
end)

HealthButton.MouseButton1Click:Connect(function()
    local localPlayer = game.Players.LocalPlayer
    if localPlayer.Character and localPlayer.Character:FindFirstChild("Humanoid") then
        local health = localPlayer.Character.Humanoid.Health
        local maxHealth = localPlayer.Character.Humanoid.MaxHealth
        local percentage = (health / maxHealth) * 100
        
        game.StarterGui:SetCore("ChatMakeSystemMessage", {
            Text = string.format("Sua vida: %.1f%%", percentage),
            Color = Color3.new(0, 1, 0)
        })
    end
end)

AimCircleButton.MouseButton1Click:Connect(function()
    AimCircle.Visible = not AimCircle.Visible
end)
if game.PlaceId == 2753915549 then
    World1 = true
elseif game.PlaceId == 4442272183 then
    World2 = true
elseif game.PlaceId == 7449423635 then
    World3 = true
else
    game:GetService("Players").LocalPlayer:Kick("Do not Support, Please wait...")
end

function CheckQuest() 
    MyLevel = game:GetService("Players").LocalPlayer.Data.Level.Value

    if World1 then

        if MyLevel == 1 or MyLevel <= 9 then

            Mon = "Bandit"
            LevelQuest = 1
            NameQuest = "BanditQuest1"
            NameMon = "Bandit"

            CFrameQuest = CFrame.new(
                1059.37195,
                15.4495068,
                1550.4231
            )

            CFrameMon = CFrame.new(
                1045.962646484375,
                27.00250816345215,
                1560.8203125
            )

        elseif MyLevel == 10 or MyLevel <= 14 then

            Mon = "Monkey"
            LevelQuest = 1
            NameQuest = "JungleQuest"
            NameMon = "Monkey"

            CFrameQuest = CFrame.new(
                -1598.08911,
                35.5501175,
                153.377838
            )

            CFrameMon = CFrame.new(
                -1448.51806640625,
                67.85301208496094,
                11.46579647064209
            )

        elseif MyLevel == 15 or MyLevel <= 29 then

            Mon = "Gorilla"
            LevelQuest = 2
            NameQuest = "JungleQuest"
            NameMon = "Gorilla"

            CFrameQuest = CFrame.new(
                -1598.08911,
                35.5501175,
                153.377838
            )

            CFrameMon = CFrame.new(
                -1129.8836669921875,
                40.46354675292969,
                -525.4237060546875
            )

        elseif MyLevel == 30 or MyLevel <= 39 then

            Mon = "Pirate"
            LevelQuest = 1
            NameQuest = "BuggyQuest1"
            NameMon = "Pirate"

            CFrameQuest = CFrame.new(
                -1141.07483,
                4.10001802,
                3831.5498
            )

            CFrameMon = CFrame.new(
                -1103.513427734375,
                13.752052307128906,
                3896.091064453125
            )

        elseif MyLevel == 40 or MyLevel <= 59 then

            Mon = "Brute"
            LevelQuest = 2
            NameQuest = "BuggyQuest1"
            NameMon = "Brute"

            CFrameQuest = CFrame.new(
                -1141.07483,
                4.10001802,
                3831.5498
            )

            CFrameMon = CFrame.new(
                -1140.083740234375,
                14.809885025024414,
                4322.92138671875
            )

        elseif MyLevel == 60 or MyLevel <= 74 then

            Mon = "Desert Bandit"
            LevelQuest = 1
            NameQuest = "DesertQuest"
            NameMon = "Desert Bandit"

            CFrameQuest = CFrame.new(
                894.488647,
                5.14000702,
                4392.43359
            )

            CFrameMon = CFrame.new(
                924.7998046875,
                6.44867467880249,
                4481.5859375
            )1
            NameQuest = "FishmanQuest"
            NameMon = "Fishman Warrior"
            CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
            CFrameMon = CFrame.new(60878.30078125, 18.482830047607422, 1543.7574462890625)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
            end
        elseif MyLevel == 400 or MyLevel <= 449 then
            Mon = "Fishman Commando"
            LevelQuest = 2
            NameQuest = "FishmanQuest"
            NameMon = "Fishman Commando"
            CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
            CFrameMon = CFrame.new(61922.6328125, 18.482830047607422, 1493.934326171875)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
            end
        elseif MyLevel == 450 or MyLevel <= 474 then
            Mon = "God's Guard"
            LevelQuest = 1
            NameQuest = "SkyExp1Quest"
            NameMon = "God's Guard"
            CFrameQuest = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
            CFrameMon = CFrame.new(-4710.04296875, 845.2769775390625, -1927.3079833984375)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
            end
        elseif MyLevel == 475 or MyLevel <= 524 then
            Mon = "Shanda"
            LevelQuest = 2
            NameQuest = "SkyExp1Quest"
            NameMon = "Shanda"
            CFrameQuest = CFrame.new(-7859.09814, 5544.19043, -381.476196, -0.422592998, 0, 0.906319618, 0, 1, 0, -0.906319618, 0, -0.422592998)
            CFrameMon = CFrame.new(-7678.48974609375, 5566.40380859375, -497.2156066894531)
            if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
            end
        elseif MyLevel == 525 or MyLevel <= 549 then
            Mon = "Royal Squad"
            LevelQuest = 1
            NameQuest = "SkyExp2Quest"
            NameMon = "Royal Squad"
            CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            CFrameMon = CFrame.new(-7624.25244140625, 5658.13330078125, -1467.354248046875)
        elseif MyLevel == 550 or MyLevel <= 624 then
            Mon = "Royal Soldier"
            LevelQuest = 2
            NameQuest = "SkyExp2Quest"
            NameMon = "Royal Soldier"
            CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            CFrameMon = CFrame.new(-7836.75341796875, 5645.6640625, -1790.6236572265625)
        elseif MyLevel == 625 or MyLevel <= 649 then
            Mon = "Galley Pirate"
            LevelQuest = 1
            NameQuest = "FountainQuest"
            NameMon = "Galley Pirate"
            CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
            CFrameMon = CFrame.new(5551.02197265625, 78.90135192871094, 3930.412841796875)
        elseif MyLevel >= 650 then
            Mon = "Galley Captain"
            LevelQuest
            -- CONFIG
_G.AutoFarm = false
_G.SelectWeapon = "Combat"
DistanceMob = 20

-- CRIAR GUI
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local ToggleButton = Instance.new("TextButton")
local WeaponBox = Instance.new("TextBox")
local HideButton = Instance.new("TextButton")

-- PARENT
ScreenGui.Parent = game.CoreGui

-- MAIN FRAME
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
MainFrame.Position = UDim2.new(0.35, 0, 0.3, 0)
MainFrame.Size = UDim2.new(0, 300, 0, 200)
MainFrame.Active = true
MainFrame.Draggable = true

-- TITLE
Title.Parent = MainFrame
Title.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
Title.Size = UDim2.new(1, 0, 0, 40)
Title.Font = Enum.Font.GothamBold
Title.Text = "Lucas Script"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.TextSize = 20

-- BOTÃO AUTO FARM
ToggleButton.Parent = MainFrame
ToggleButton.Position = UDim2.new(0.1, 0, 0.35, 0)
ToggleButton.Size = UDim2.new(0, 240, 0, 40)
ToggleButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
ToggleButton.TextColor3 = Color3.fromRGB(255,255,255)
ToggleButton.Font = Enum.Font.GothamBold
ToggleButton.TextSize = 18
ToggleButton.Text = "Auto Farm: OFF"

ToggleButton.MouseButton1Click:Connect(function()
    _G.AutoFarm = not _G.AutoFarm

    if _G.AutoFarm then
        ToggleButton.Text = "Auto Farm: ON"
        ToggleButton.BackgroundColor3 = Color3.fromRGB(0,170,0)
    else
        ToggleButton.Text = "Auto Farm: OFF"
        ToggleButton.BackgroundColor3 = Color3.fromRGB(40,40,40)
    end
end)

-- TEXTBOX ARMA
WeaponBox.Parent = MainFrame
WeaponBox.Position = UDim2.new(0.1, 0, 0.65, 0)
WeaponBox.Size = UDim2.new(0, 240, 0, 35)
WeaponBox.BackgroundColor3 = Color3.fromRGB(30,30,30)
WeaponBox.TextColor3 = Color3.fromRGB(255,255,255)
WeaponBox.Font = Enum.Font.Gotham
WeaponBox.TextSize = 16
WeaponBox.PlaceholderText = "Nome da arma"
WeaponBox.Text = _G.SelectWeapon

WeaponBox.FocusLost:Connect(function()
    _G.SelectWeapon = WeaponBox.Text
end)

-- BOTÃO ESCONDER
HideButton.Parent = ScreenGui
HideButton.Position = UDim2.new(0, 10, 0.4, 0)
HideButton.Size = UDim2.new(0, 120, 0, 35)
HideButton.BackgroundColor3 = Color3.fromRGB(255,0,0)
HideButton.Text = "Mostrar / Esconder"
HideButton.TextColor3 = Color3.fromRGB(255,255,255)
HideButton.Font = Enum.Font.GothamBold
HideButton.TextSize = 14

HideButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
end)
