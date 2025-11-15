local Rep = game:GetService("ReplicatedStorage")
local Player = game.Players.LocalPlayer
local Mouse = Player:GetMouse()

local PlantFolder = Rep:WaitForChild("Plantas")
local spawnEvent = Rep:WaitForChild("SpawnPlanta")

-- Criar GUI
local ScreenGui = script.Parent
local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 250, 0, 300)
Frame.Position = UDim2.new(0, 20, 0.5, -150)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.Parent = ScreenGui

local UIList = Instance.new("UIListLayout")
UIList.Parent = Frame
UIList.Padding = UDim.new(0, 5)

-- Criar botões automaticamente para cada planta
for _, plant in pairs(PlantFolder:GetChildren()) do
    local botao = Instance.new("TextButton")
    botao.Size = UDim2.new(1, -10, 0, 40)
    botao.Text = "Spawn: " .. plant.Name
    botao.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    botao.TextColor3 = Color3.new(1, 1, 1)
    botao.Parent = Frame

    botao.MouseButton1Click:Connect(function()
        local pos = Mouse.Hit.Position
        spawnEvent:FireServer(plant.Name, pos)
    end)
end# Hghgrhfh
