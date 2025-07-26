local UserInputService = game:GetService("UserInputService")
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

-- Enable Infinite Jump
local infJumpEnabled = true

-- Listen for Jump Request
UserInputService.JumpRequest:Connect(function()
    if infJumpEnabled then
        -- Force the humanoid to jump, even in mid-air
        humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
    end
end)

-- Optional: Toggle Infinite Jump with a key (e.g., "J")
UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if input.KeyCode == Enum.KeyCode.J and not gameProcessed then
        infJumpEnabled = not infJumpEnabled
        if infJumpEnabled then
            print("Infinite Jump ENABLED")
        else
            print("Infinite Jump DISABLED")
        end
    end
end)
