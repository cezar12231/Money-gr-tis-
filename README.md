-- Variável de controle
local ativado = false

-- Criar a interface
local ScreenGui = Instance.new("ScreenGui", game.Players.LocalPlayer:WaitForChild("PlayerGui"))
ScreenGui.Name = "AutoFarmUI"

local Frame = Instance.new("Frame", ScreenGui)
Frame.Size = UDim2.new(0, 200, 0, 140)
Frame.Position = UDim2.new(0, 20, 0, 200)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.BorderSizePixel = 0

local Title = Instance.new("TextLabel", Frame)
Title.Size = UDim2.new(1, 0, 0, 30)
Title.BackgroundTransparency = 1
Title.Text = "💸 Auto Claim Money"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 16

local Credit = Instance.new("TextLabel", Frame)
Credit.Size = UDim2.new(1, 0, 0, 20)
Credit.Position = UDim2.new(0, 0, 0, 30)
Credit.BackgroundTransparency = 1
Credit.Text = "by Cezar✌🏻"
Credit.TextColor3 = Color3.fromRGB(150, 150, 150)
Credit.Font = Enum.Font.Gotham
Credit.TextSize = 13

local Button = Instance.new("TextButton", Frame)
Button.Size = UDim2.new(0.9, 0, 0, 40)
Button.Position = UDim2.new(0.05, 0, 0.6, 0)
Button.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.Font = Enum.Font.Gotham
Button.TextSize = 14
Button.Text = "Ativar Farm"

-- Função de repetição
local function repetir()
    while ativado do
        local args = {
            [1] = 1
        }

        game:GetService("ReplicatedStorage").GiveClaimMoney:FireServer(unpack(args))
        task.wait(0.1)
    end
end

-- Lógica do botão
Button.MouseButton1Click:Connect(function()
    ativado = not ativado
    if ativado then
        Button.Text = "Desativar Farm"
        repetir()
    else
        Button.Text = "Ativar Farm"
    end
end)
