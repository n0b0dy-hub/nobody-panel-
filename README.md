-- n0b0dy panel
-- Admin panel exemplo
-- Interface criada com Instance.new

local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

----------------------------------------------------
-- ScreenGui
----------------------------------------------------

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "n0b0dyPanel"
screenGui.Parent = playerGui
screenGui.ResetOnSpawn = false

----------------------------------------------------
-- Botão Abrir / Fechar
----------------------------------------------------

local toggleButton = Instance.new("TextButton")
toggleButton.Parent = screenGui
toggleButton.Size = UDim2.new(0,120,0,40)
toggleButton.Position = UDim2.new(0,10,0.5,-20)
toggleButton.BackgroundColor3 = Color3.fromRGB(20,20,20)
toggleButton.Text = "n0b0dy"
toggleButton.TextColor3 = Color3.new(1,1,1)
toggleButton.TextScaled = true
toggleButton.Font = Enum.Font.SourceSansBold
toggleButton.BorderSizePixel = 0

----------------------------------------------------
-- Frame principal
----------------------------------------------------

local mainFrame = Instance.new("Frame")
mainFrame.Parent = screenGui
mainFrame.Size = UDim2.new(0,320,0,320)
mainFrame.Position = UDim2.new(0,150,0.5,-160)
mainFrame.BackgroundColor3 = Color3.fromRGB(25,25,25)
mainFrame.BorderSizePixel = 0
mainFrame.Visible = false

----------------------------------------------------
-- Título
----------------------------------------------------

local title = Instance.new("TextLabel")
title.Parent = mainFrame
title.Size = UDim2.new(1,0,0,40)
title.BackgroundColor3 = Color3.fromRGB(15,15,15)
title.Text = "n0b0dy panel"
title.TextColor3 = Color3.new(1,1,1)
title.TextScaled = true
title.Font = Enum.Font.SourceSansBold
title.BorderSizePixel = 0

----------------------------------------------------
-- Velocidade
----------------------------------------------------

local speedBox = Instance.new("TextBox")
speedBox.Parent = mainFrame
speedBox.Size = UDim2.new(1,-20,0,30)
speedBox.Position = UDim2.new(0,10,0,60)
speedBox.BackgroundColor3 = Color3.fromRGB(40,40,40)
speedBox.TextColor3 = Color3.new(1,1,1)
speedBox.PlaceholderText = "WalkSpeed"
speedBox.Text = ""
speedBox.TextScaled = true
speedBox.Font = Enum.Font.SourceSans

local speedButton = Instance.new("TextButton")
speedButton.Parent = mainFrame
speedButton.Size = UDim2.new(1,-20,0,30)
speedButton.Position = UDim2.new(0,10,0,95)
speedButton.BackgroundColor3 = Color3.fromRGB(60,60,60)
speedButton.Text = "Set Speed"
speedButton.TextColor3 = Color3.new(1,1,1)
speedButton.TextScaled = true
speedButton.Font = Enum.Font.SourceSansBold

----------------------------------------------------
-- Sky ID
----------------------------------------------------

local skyBox = Instance.new("TextBox")
skyBox.Parent = mainFrame
skyBox.Size = UDim2.new(1,-20,0,30)
skyBox.Position = UDim2.new(0,10,0,140)
skyBox.BackgroundColor3 = Color3.fromRGB(40,40,40)
skyBox.TextColor3 = Color3.new(1,1,1)
skyBox.PlaceholderText = "Sky ID"
skyBox.Text = ""
skyBox.TextScaled = true
skyBox.Font = Enum.Font.SourceSans

local skyButton = Instance.new("TextButton")
skyButton.Parent = mainFrame
skyButton.Size = UDim2.new(1,-20,0,30)
skyButton.Position = UDim2.new(0,10,0,175)
skyButton.BackgroundColor3 = Color3.fromRGB(60,60,60)
skyButton.Text = "Set Sky"
skyButton.TextColor3 = Color3.new(1,1,1)
skyButton.TextScaled = true
skyButton.Font = Enum.Font.SourceSansBold

----------------------------------------------------
-- Kill botão
----------------------------------------------------

local killButton = Instance.new("TextButton")
killButton.Parent = mainFrame
killButton.Size = UDim2.new(1,-20,0,35)
killButton.Position = UDim2.new(0,10,0,225)
killButton.BackgroundColor3 = Color3.fromRGB(120,40,40)
killButton.Text = "Kill Character"
killButton.TextColor3 = Color3.new(1,1,1)
killButton.TextScaled = true
killButton.Font = Enum.Font.SourceSansBold

----------------------------------------------------
-- Função abrir/fechar
----------------------------------------------------

toggleButton.MouseButton1Click:Connect(function()

	mainFrame.Visible = not mainFrame.Visible

end)

----------------------------------------------------
-- Função velocidade
----------------------------------------------------

speedButton.MouseButton1Click:Connect(function()

	local character = player.Character

	if character then

		local humanoid = character:FindFirstChildOfClass("Humanoid")

		if humanoid then

			local speed = tonumber(speedBox.Text)

			if speed then
				humanoid.WalkSpeed = speed
			end

		end

	end

end)

----------------------------------------------------
-- Função Sky
----------------------------------------------------

skyButton.MouseButton1Click:Connect(function()

	local id = skyBox.Text

	if id ~= "" then

		local sky = game.Lighting:FindFirstChildOfClass("Sky")

		if not sky then
			sky = Instance.new("Sky")
			sky.Parent = game.Lighting
		end

		local asset = "rbxassetid://"..id

		sky.SkyboxBk = asset
		sky.SkyboxDn = asset
		sky.SkyboxFt = asset
		sky.SkyboxLf = asset
		sky.SkyboxRt = asset
		sky.SkyboxUp = asset

	end

end)

----------------------------------------------------
-- Função Kill
----------------------------------------------------

killButton.MouseButton1Click:Connect(function()

	local character = player.Character

	if character then

		local humanoid = character:FindFirstChildOfClass("Humanoid")

		if humanoid then
			humanoid.Health = 0
		end

	end

end)
