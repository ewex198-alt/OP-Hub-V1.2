local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("script ภาษาไทยผู้สร้าง [แสตมป์]", "DarkTheme")
local Tab = Window:NewTab("โซนพระเจ้า")
local Section = Tab:NewSection("โปรพระเจ้า")
Section:NewTextBox("โปรวิ่งเร็ว", "TextboxInfo", function(txt)
	game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = txt
end)

Section:NewButton("โปรบินได้", "ButtonInfo", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/XNEOFF/FlyGuiV3/main/FlyGuiV3.txt"))()
end)

Section:NewButton("โปรมองทะลุผู้เล่น", "ButtonInfo", function()
    -- Script de ESP

local player = game.Players.LocalPlayer
local ESPs = {}

-- Função para criar o ESP
local function createESP(targetPlayer)
    if targetPlayer.Character and targetPlayer.Character:FindFirstChild("Head") then
        local BillboardGui = Instance.new("BillboardGui")
        BillboardGui.Name = "ESP"
        BillboardGui.Parent = targetPlayer.Character.Head
        BillboardGui.AlwaysOnTop = true
        BillboardGui.Size = UDim2.new(0, 100, 0, 40)
        BillboardGui.StudsOffset = Vector3.new(0, 2, 0)

        local NameTag = Instance.new("TextLabel")
        NameTag.Parent = BillboardGui
        NameTag.BackgroundTransparency = 1
        NameTag.Size = UDim2.new(1, 0, 0.5, 0)
        NameTag.Text = targetPlayer.Name
        NameTag.TextColor3 = Color3.fromRGB(255, 255, 255)
        NameTag.TextStrokeTransparency = 0.5
        NameTag.TextScaled = true

        local HealthTag = Instance.new("TextLabel")
        HealthTag.Parent = BillboardGui
        HealthTag.BackgroundTransparency = 1
        HealthTag.Position = UDim2.new(0, 0, 0.5, 0)
        HealthTag.Size = UDim2.new(1, 0, 0.5, 0)
        HealthTag.TextColor3 = Color3.fromRGB(255, 0, 0)
        HealthTag.TextStrokeTransparency = 0.5
        HealthTag.TextScaled = true

        game:GetService("RunService").RenderStepped:Connect(function()
            if targetPlayer.Character and targetPlayer.Character:FindFirstChild("Humanoid") then
                HealthTag.Text = "HP: " .. math.floor(targetPlayer.Character.Humanoid.Health)
                local distance = (player.Character.HumanoidRootPart.Position - targetPlayer.Character.HumanoidRootPart.Position).magnitude
                NameTag.Text = targetPlayer.Name .. " (" .. math.floor(distance) .. "m)"
            end
        end)

        table.insert(ESPs, BillboardGui)
    end
end

-- Aplica ESP a todos os jogadores
for _, targetPlayer in pairs(game.Players:GetPlayers()) do
    if targetPlayer ~= player then
        createESP(targetPlayer)
    end
end

game.Players.PlayerAdded:Connect(function(targetPlayer)
    targetPlayer.CharacterAdded:Connect(function()
        wait(1)
        createESP(targetPlayer)
    end)
end)

-- Função para desativar ESP
local function disableESP()
    for _, esp in pairs(ESPs) do
        esp:Destroy()
    end
    ESPs = {}
end

-- Desative o ESP chamando disableESP() quando necessário
end)


local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "ScreenGui"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

local Toggle = Instance.new("TextButton")
Toggle.Name = "Toggle"
Toggle.Parent = ScreenGui
Toggle.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Toggle.Position = UDim2.new(0, 0, 0.454706937, 0)
Toggle.Size = UDim2.new(0, 90, 0, 38)
Toggle.Font = Enum.Font.SourceSans
Toggle.Text = "ปิด Ui"
Toggle.TextColor3 = Color3.fromRGB(248, 248, 248)
Toggle.TextSize = 28.000
Toggle.Draggable = true
Toggle.MouseButton1Click:Connect(function()
    if Toggle.Text == "เปิด Ui" then
        Toggle.Text = "ปิด Ui"
    else
        Toggle.Text = "เปิด Ui"
    end
    Library:ToggleUI()
end)

local Corner = Instance.new("UICorner")
Corner.Name = "Corner"
Corner.Parent = Toggle
