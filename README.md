--// Caio_hub - Estilo Atual Premium Black + 2 Botões (F e L)

local Players = game:GetService("Players")
local lp = Players.LocalPlayer
local char = lp.Character or lp.CharacterAdded:Wait()
local VirtualInputManager = game:GetService("VirtualInputManager")
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")

-- GUI principal
local gui = Instance.new("ScreenGui", game.CoreGui)
gui.Name = "Caio_hub"

-- Frame principal
local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 240, 0, 235)
frame.Position = UDim2.new(0.5, -120, 0.5, -110)
frame.BackgroundColor3 = Color3.fromRGB(12, 12, 12)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true

local frameCorner = Instance.new("UICorner", frame)
frameCorner.CornerRadius = UDim.new(0, 14)

-- Topbar
local topBar = Instance.new("Frame", frame)
topBar.Size = UDim2.new(1, 0, 0, 32)
topBar.BackgroundColor3 = Color3.fromRGB(18, 18, 18)
topBar.BorderSizePixel = 0

local cornerTB = Instance.new("UICorner", topBar)
cornerTB.CornerRadius = UDim.new(0, 14)

-- Título
local title = Instance.new("TextLabel", topBar)
title.Size = UDim2.new(1, -20, 1, 0)
title.Position = UDim2.new(0, 10, 0, 0)
title.BackgroundTransparency = 1
title.Text = "Caio_hub"
title.Font = Enum.Font.GothamBold
title.TextSize = 21
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextXAlignment = Enum.TextXAlignment.Left


----------------------------------------------------------
-- BOTÃO 1 — DEVOUR (F)
----------------------------------------------------------

local btn1 = Instance.new("TextButton", frame)
btn1.Size = UDim2.new(1, -30, 0, 75)
btn1.Position = UDim2.new(0, 15, 0, 55)
btn1.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
btn1.BorderSizePixel = 0
btn1.Text = ""
btn1.AutoButtonColor = true

local b1corner = Instance.new("UICorner", btn1)
b1corner.CornerRadius = UDim.new(0, 10)

-- Título botão 1
local btn1Title = Instance.new("TextLabel", btn1)
btn1Title.Size = UDim2.new(1, 0, 0.5, 0)
btn1Title.Position = UDim2.new(0, 0, 0, 5)
btn1Title.BackgroundTransparency = 1
btn1Title.Text = "Devoure"
btn1Title.Font = Enum.Font.GothamBold
btn1Title.TextSize = 23
btn1Title.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Subtítulo F
local btn1Sub = Instance.new("TextLabel", btn1)
btn1Sub.Size = UDim2.new(1, 0, 0.35, 0)
btn1Sub.Position = UDim2.new(0, 0, 0.55, -5)
btn1Sub.BackgroundTransparency = 1
btn1Sub.Text = "Pressione F"
btn1Sub.Font = Enum.Font.Gotham
btn1Sub.TextSize = 15
btn1Sub.TextColor3 = Color3.fromRGB(170, 170, 170)


-- Função Devoure
local function Devoure()
    task.spawn(function()

        -- Equipar todos
        for _,tool in ipairs(lp.Backpack:GetChildren()) do
            if tool:IsA("Tool") then
                tool.Parent = char
            end
        end

        task.wait(0.2)

        -- click
        VirtualInputManager:SendMouseButtonEvent(500,500,0,true,game,1)
        task.wait(0.05)
        VirtualInputManager:SendMouseButtonEvent(500,500,0,false,game,1)

        task.wait(0.6)

        -- Spamar todos os tools equipados
        for _,tool in ipairs(char:GetChildren()) do
            if tool:IsA("Tool") then
                VirtualInputManager:SendMouseButtonEvent(500,500,0,true,game,1)
                task.wait(0.01)
                VirtualInputManager:SendMouseButtonEvent(500,500,0,false,game,1)
            end
        end
    end)
end

btn1.MouseButton1Click:Connect(Devoure)

UIS.InputBegan:Connect(function(input, gpe)
    if gpe then return end
    if input.KeyCode == Enum.KeyCode.F then
        Devoure()
    end
end)


----------------------------------------------------------
-- BOTÃO 2 — ANTI-LAG SUPREMO (L)
----------------------------------------------------------

local btn2 = Instance.new("TextButton", frame)
btn2.Size = UDim2.new(1, -30, 0, 75)
btn2.Position = UDim2.new(0, 15, 0, 140)
btn2.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
btn2.BorderSizePixel = 0
btn2.Text = ""
btn2.AutoButtonColor = true

local b2corner = Instance.new("UICorner", btn2)
b2corner.CornerRadius = UDim.new(0, 10)

-- Título do botão 2
local btn2Title = Instance.new("TextLabel", btn2)
btn2Title.Size = UDim2.new(1, 0, 0.5, 0)
btn2Title.Position = UDim2.new(0, 0, 0, 5)
btn2Title.BackgroundTransparency = 1
btn2Title.Text = "Anti-Lag Supremo"
btn2Title.Font = Enum.Font.GothamBold
btn2Title.TextSize = 21
btn2Title.TextColor3 = Color3.fromRGB(255, 255, 255)

-- Subtítulo L
local btn2Sub = Instance.new("TextLabel", btn2)
btn2Sub.Size = UDim2.new(1, 0, 0.35, 0)
btn2Sub.Position = UDim2.new(0, 0, 0.55, -5)
btn2Sub.BackgroundTransparency = 1
btn2Sub.Text = "Pressione L"
btn2Sub.Font = Enum.Font.Gotham
btn2Sub.TextSize = 15
btn2Sub.TextColor3 = Color3.fromRGB(170, 170, 170)

local function AntiLag()
    for _,obj in ipairs(workspace:GetDescendants()) do
        if obj:IsA("ParticleEmitter")
        or obj:IsA("Smoke")
        or obj:IsA("Fire")
        or obj:IsA("Sparkles")
        or obj:IsA("Trail")
        or obj:IsA("Beam")
        or obj:IsA("Explosion")
        or obj:IsA("Decal")
        or obj:IsA("Texture")
        or obj:IsA("PointLight")
        or obj:IsA("SpotLight")
        or obj:IsA("SurfaceLight")
        or obj:IsA("Sound") then
            pcall(function() obj:Destroy() end)
        end
    end
end

btn2.MouseButton1Click:Connect(AntiLag)

UIS.InputBegan:Connect(function(input,gpe)
    if gpe then return end
    if input.KeyCode == Enum.KeyCode.L then
        AntiLag()
    end
end)
