local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/ZeianRussell/Kavo-UI-Library/main/Movable.source.lua"))()
local Window = Library.CreateLib("Script v1 ภาษาไทยผู้พัฒนา [EWEX222]", colors)
local Tab = Window:NewTab("โซนพระเจ้า")
local Section = Tab:NewSection("โปรพระเจ้า")

Section:NewTextBox("โปรวิ่งเร็ว", "TextboxInfo", function(txt)
	game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = txt
end)

Section:NewButton("โปรบิน", "ButtonInfo", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/XNEOFF/FlyGuiV3/main/FlyGuiV3.txt"))()
end)

Section:NewButton("โปรมองทะลุผู้เล่น", "ButtonInfo", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/5Q5yC3VZ"))()
end)

Section:NewButton("โปรล่องหน", "ButtonInfo", function()
    loadstring(game:HttpGet('https://pastebin.com/raw/3Rnd9rHf'))()
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
Toggle.Text = "ปิด"
Toggle.TextColor3 = Color3.fromRGB(248, 248, 248)
Toggle.TextSize = 28.000
Toggle.Draggable = true
Toggle.MouseButton1Click:Connect(function()
    if Toggle.Text == "เปิด" then
        Toggle.Text = "ปิด"
    else
        Toggle.Text = "เปิด"
    end
    Library:ToggleUI()
end)

local Corner = Instance.new("UICorner")
Corner.Name = "Corner"
Corner.Parent = Toggle
