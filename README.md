local ScreenGui = Instance.new("ScreenGui") -- Create a ScreenGui to hold the hub
local Frame = Instance.new("Frame") -- Create a frame for the hub
local CompleteButton = Instance.new("TextButton") -- Create a button to complete the parkour

-- Set properties for the ScreenGui
ScreenGui.Name = "ParkourHub"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Set properties for the Frame
Frame.Size = UDim2.new(0, 300, 0, 200) -- Medium size
Frame.Position = UDim2.new(0.5, -150, 0.5, -100) -- Centered on screen
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50) -- Dark background
Frame.Parent = ScreenGui

-- Set properties for the CompleteButton
CompleteButton.Size = UDim2.new(0, 200, 0, 50) -- Button size
CompleteButton.Position = UDim2.new(0.5, -100, 0.5, -25) -- Centered in the Frame
CompleteButton.Text = "Complete Parkour" -- Button text
CompleteButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0) -- Green background
CompleteButton.Parent = Frame

-- Function to complete the parkour
local function completeParkour()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait() -- Get the player's character
    local parkourEndPoint = game.Workspace:FindFirstChild("ParkourEnd") -- Replace with actual end point

    if parkourEndPoint then
        character.HumanoidRootPart.CFrame = parkourEndPoint.CFrame -- Teleport to the end point
    else
        warn("Parkour end point not found!") -- Warn if the end point doesn't exist
    end
end

-- Connect the button to the completeParkour function
CompleteButton.MouseButton1Click:Connect(completeParkour)
