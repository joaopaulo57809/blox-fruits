-- Inicialização do painel
local player = game.Players.LocalPlayer

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ToggleButton = Instance.new("TextButton")
local FarmLevelButton = Instance.new("TextButton")
local AutoFarmHeartsButton = Instance.new("TextButton")
local AutoFarmEnemiesButton = Instance.new("TextButton")
local AutoFarmFactoryButton = Instance.new("TextButton")
local AutoFarmEctoplasmButton = Instance.new("TextButton")
local AutoChestsButton = Instance.new("TextButton")
local ESPPlayersButton = Instance.new("TextButton")
local ESPFruitsButton = Instance.new("TextButton")
local ESPChestsButton = Instance.new("TextButton")

ScreenGui.Parent = player:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Position = UDim2.new(0.02, 0, 0.1, 0)
Frame.Size = UDim2.new(0, 300, 0, 500)

-- Função para criar botões
local function createButton(button, text, position)
    button.Parent = Frame
    button.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
    button.Size = UDim2.new(1, 0, 0, 40)
    button.Position = UDim2.new(0, 0, position, 0)
    button.Font = Enum.Font.SourceSans
    button.Text = text
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.TextScaled = true
end

-- Criação dos botões
createButton(ToggleButton, "Aimbot: OFF", 0.0)
createButton(FarmLevelButton, "Farmar Níveis Automático", 0.1)
createButton(AutoFarmHeartsButton, "Auto Farm Hearts", 0.2)
createButton(AutoFarmEnemiesButton, "Farmar Inimigos Próximos", 0.3)
createButton(AutoFarmFactoryButton, "Fábrica Automática", 0.4)
createButton(AutoFarmEctoplasmButton, "Farmar Ectoplasma", 0.5)
createButton(AutoChestsButton, "Auto Baús [Tween]", 0.6)
createButton(ESPPlayersButton, "ESP Jogadores", 0.7)
createButton(ESPFruitsButton, "ESP Frutas", 0.8)
createButton(ESPChestsButton, "ESP Baús", 0.9)

-- Função para alternar aimbot
ToggleButton.MouseButton1Click:Connect(function()
    aimbotEnabled = not aimbotEnabled
    ToggleButton.Text = aimbotEnabled and "Aimbot: ON" or "Aimbot: OFF"
end)

-- Funções para as ações dos botões
FarmLevelButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para farmar níveis automaticamente
end)

AutoFarmHeartsButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para farmar corações automaticamente
end)

AutoFarmEnemiesButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para farmar inimigos próximos automaticamente
end)

AutoFarmFactoryButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para farmar a fábrica automaticamente
end)

AutoFarmEctoplasmButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para farmar ectoplasmas automaticamente
end)

AutoChestsButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para farmar baús automaticamente
end)

ESPPlayersButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para ESP de jogadores
end)

ESPFruitsButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para ESP de frutas
end)

ESPChestsButton.MouseButton1Click:Connect(function()
    -- Adicione aqui o código para ESP de baús
end)

-- Loop para buscar o alvo mais próximo e aplicar aimbot
game:GetService("RunService").RenderStepped:Connect(function()
    if aimbotEnabled then
        local closestTarget = nil
        local closestDistance = math.huge
        
        for _, v in pairs(game.Workspace:GetChildren()) do
            if v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
                local distance = (v.HumanoidRootPart.Position - player.Character.HumanoidRootPart.Position).Magnitude
                if distance < closestDistance then
                    closestDistance = distance
                    closestTarget = v
                end
            end
        end
        
        if closestTarget then
            local mouse = player:GetMouse()
            mouse.TargetFilter = closestTarget
            mouse.Hit = closestTarget.CFrame
        end
    end
end)
