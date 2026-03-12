local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer
local playerGui = player.PlayerGui

if playerGui:FindFirstChild("ClockQuizHub") then
    playerGui.ClockQuizHub:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "ClockQuizHub"
ScreenGui.ResetOnSpawn = false
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = playerGui

local Main = Instance.new("Frame")
Main.Size = UDim2.new(0, 260, 0, 210)
Main.Position = UDim2.new(0.5, -130, 0.5, -105)
Main.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
Main.BorderSizePixel = 0
Main.Active = true
Main.Draggable = true
Main.Parent = ScreenGui

Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 6)
local s = Instance.new("UIStroke", Main)
s.Color = Color3.fromRGB(255,255,255)
s.Thickness = 1.5

local Title = Instance.new("TextLabel", Main)
Title.Size = UDim2.new(1,-40,0,36)
Title.Position = UDim2.new(0,10,0,0)
Title.BackgroundTransparency = 1
Title.Text = "🕐Chronos Quiz Hub🕟"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.TextSize = 15
Title.Font = Enum.Font.GothamBold
Title.TextXAlignment = Enum.TextXAlignment.Left

local Line = Instance.new("Frame", Main)
Line.Size = UDim2.new(1,-20,0,1)
Line.Position = UDim2.new(0,10,0,36)
Line.BackgroundColor3 = Color3.fromRGB(60,60,60)
Line.BorderSizePixel = 0

local CloseBtn = Instance.new("TextButton", Main)
CloseBtn.Size = UDim2.new(0,28,0,28)
CloseBtn.Position = UDim2.new(1,-34,0,4)
CloseBtn.BackgroundColor3 = Color3.fromRGB(30,30,30)
CloseBtn.Text = "✕"
CloseBtn.TextColor3 = Color3.fromRGB(200,200,200)
CloseBtn.TextSize = 13
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.BorderSizePixel = 0
Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0,4)
CloseBtn.MouseButton1Click:Connect(function()
    TweenService:Create(Main, TweenInfo.new(0.2), {
        Size = UDim2.new(0,0,0,0),
        Position = UDim2.new(0.5,0,0.5,0)
    }):Play()
    task.wait(0.2)
    ScreenGui:Destroy()
end)

local Status = Instance.new("TextLabel", Main)
Status.Size = UDim2.new(1,-20,0,20)
Status.Position = UDim2.new(0,10,0,44)
Status.BackgroundTransparency = 1
Status.Text = "Use in Chapter 4 - Stage 30 \"Utopia Teapots\""
Status.TextColor3 = Color3.fromRGB(150,150,150)
Status.TextSize = 11
Status.Font = Enum.Font.Gotham
Status.TextXAlignment = Enum.TextXAlignment.Left

local QuizBtn = Instance.new("TextButton", Main)
QuizBtn.Size = UDim2.new(1,-20,0,34)
QuizBtn.Position = UDim2.new(0,10,0,70)
QuizBtn.BackgroundColor3 = Color3.fromRGB(20,20,20)
QuizBtn.Text = "🕐  Clock Quiz"
QuizBtn.TextColor3 = Color3.fromRGB(255,255,255)
QuizBtn.TextSize = 13
QuizBtn.Font = Enum.Font.GothamBold
QuizBtn.BorderSizePixel = 0
Instance.new("UICorner", QuizBtn).CornerRadius = UDim.new(0,5)
local qs = Instance.new("UIStroke", QuizBtn)
qs.Color = Color3.fromRGB(80,80,80)
qs.Thickness = 1

QuizBtn.MouseEnter:Connect(function()
    TweenService:Create(QuizBtn, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(40,40,40)}):Play()
    TweenService:Create(qs, TweenInfo.new(0.15), {Color = Color3.fromRGB(255,255,255)}):Play()
end)
QuizBtn.MouseLeave:Connect(function()
    TweenService:Create(QuizBtn, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(20,20,20)}):Play()
    TweenService:Create(qs, TweenInfo.new(0.15), {Color = Color3.fromRGB(80,80,80)}):Play()
end)
QuizBtn.MouseButton1Click:Connect(function()
    local ok, err = pcall(function()
        if playerGui:FindFirstChild("ClockQuiz") then
            playerGui.ClockQuiz:Destroy()
        end
        local clone = game:GetService("ReplicatedStorage").Cutscenes.ClockQuiz:Clone()
        clone.Parent = playerGui
        Status.Text = "✔ Clock Quiz opened!"
        Status.TextColor3 = Color3.fromRGB(100,255,100)
        task.delay(2, function()
            Status.Text = "Use in Chapter 4 - Stage 30 \"Utopia Teapots\""
            Status.TextColor3 = Color3.fromRGB(150,150,150)
        end)
    end)
    if not ok then
        Status.Text = "✘ Error: " .. tostring(err)
        Status.TextColor3 = Color3.fromRGB(255,80,80)
    end
end)

local ToggleFrame = Instance.new("Frame", Main)
ToggleFrame.Size = UDim2.new(1,-20,0,34)
ToggleFrame.Position = UDim2.new(0,10,0,112)
ToggleFrame.BackgroundColor3 = Color3.fromRGB(20,20,20)
ToggleFrame.BorderSizePixel = 0
Instance.new("UICorner", ToggleFrame).CornerRadius = UDim.new(0,5)
local ts = Instance.new("UIStroke", ToggleFrame)
ts.Color = Color3.fromRGB(80,80,80)
ts.Thickness = 1

local ToggleLabel = Instance.new("TextLabel", ToggleFrame)
ToggleLabel.Size = UDim2.new(1,-45,1,0)
ToggleLabel.Position = UDim2.new(0,10,0,0)
ToggleLabel.BackgroundTransparency = 1
ToggleLabel.Text = "🔘  Auto Correct"
ToggleLabel.TextColor3 = Color3.fromRGB(255,255,255)
ToggleLabel.TextSize = 13
ToggleLabel.Font = Enum.Font.GothamBold
ToggleLabel.TextXAlignment = Enum.TextXAlignment.Left

local Ball = Instance.new("TextButton", ToggleFrame)
Ball.Size = UDim2.new(0,28,0,28)
Ball.Position = UDim2.new(1,-34,0.5,-14)
Ball.BackgroundColor3 = Color3.fromRGB(80,80,80)
Ball.Text = "●"
Ball.TextColor3 = Color3.fromRGB(255,255,255)
Ball.TextSize = 16
Ball.Font = Enum.Font.GothamBold
Ball.BorderSizePixel = 0
Instance.new("UICorner", Ball).CornerRadius = UDim.new(1,0)

local Result = Instance.new("TextLabel", Main)
Result.Size = UDim2.new(1,-20,0,46)
Result.Position = UDim2.new(0,10,0,154)
Result.BackgroundTransparency = 1
Result.Text = ""
Result.TextColor3 = Color3.fromRGB(100,255,100)
Result.TextSize = 18
Result.Font = Enum.Font.GothamBold
Result.TextXAlignment = Enum.TextXAlignment.Center
Result.TextWrapped = true

local sprites = game:GetService("ReplicatedStorage").Cutscenes.ClockQuiz.Sprites

local function buildImageMap(folder)
    local map = {}
    for i = 1, 12 do
        local sprite = folder:FindFirstChild(tostring(i))
        if sprite then
            map[sprite.Image] = (i == 12) and 0 or i
        end
    end
    return map
end

local autoCorrectActive = false
local hookInstalled = false

local function installHook()
    if hookInstalled then return end
    hookInstalled = true
    playerGui.ChildAdded:Connect(function(gui)
        if gui.Name == "ClockQuiz" and autoCorrectActive then
            Status.Text = "Quiz detected!"
            Status.TextColor3 = Color3.fromRGB(255,255,0)
            Result.Text = ""
            task.spawn(function()
                task.wait(2.5)
                local hourMap = buildImageMap(sprites.Hour)
                local minuteMap = buildImageMap(sprites.Minute)
                local parentFrame = gui.Frame:FindFirstChild("Question") or gui.Frame:FindFirstChild("QuestionTroll")
                if not parentFrame then
                    Status.Text = "✘ Frame not found"
                    Status.TextColor3 = Color3.fromRGB(255,80,80)
                    return
                end
                local totalHour = 0
                local totalMinute = 0
                local clockCount = 0
                for _, obj in ipairs(parentFrame:GetChildren()) do
                    if obj.Name == "Clock" then
                        local hourImg = obj:FindFirstChild("Hour")
                        local minuteImg = obj:FindFirstChild("Minute")
                        if hourImg and minuteImg then
                            local h = hourMap[hourImg.Image]
                            local m = minuteMap[minuteImg.Image]
                            if h ~= nil and m ~= nil then
                                totalHour = totalHour + h
                                totalMinute = totalMinute + m
                                clockCount = clockCount + 1
                            end
                        end
                    end
                end
                if clockCount == 0 then
                    Status.Text = "✘ No clocks found"
                    Status.TextColor3 = Color3.fromRGB(255,80,80)
                    return
                end         
                while totalMinute >= 12 do
                    totalHour = totalHour + 1
                    totalMinute = totalMinute - 12
                end
                while totalMinute < 0 do
                    totalHour = totalHour - 1
                    totalMinute = totalMinute + 12
                end
                while totalHour >= 12 do
                    totalHour = totalHour - 12
                end
                while totalHour < 0 do
                    totalHour = totalHour + 12
                end
                local choices = gui.Frame.Choices
                local correctBtn = nil
                for _, btn in ipairs(choices:GetChildren()) do
                    if btn:IsA("ImageButton") then
                        local btnHour = btn:FindFirstChild("Hour")
                        local btnMinute = btn:FindFirstChild("Minute")
                        if btnHour and btnMinute then
                            local bh = hourMap[btnHour.Image]
                            local bm = minuteMap[btnMinute.Image]
                            if bh == totalHour and bm == totalMinute then
                                correctBtn = btn
                                break
                            end
                        end
                    end
                end
                if correctBtn then
                    Status.Text = "✔ Answer found!"
                    Status.TextColor3 = Color3.fromRGB(100,255,100)
                    Result.Text = "👉 " .. correctBtn.Name .. " 👈"
                    Result.TextColor3 = Color3.fromRGB(100,255,100)
                else
                    Status.Text = "Error"
                    Status.TextColor3 = Color3.fromRGB(255,80,80)
                    Result.Text = "H: " .. totalHour .. " | M: " .. totalMinute
                    Result.TextColor3 = Color3.fromRGB(255,80,80)
                end
            end)
        end
    end)
end

Ball.MouseButton1Click:Connect(function()
    autoCorrectActive = not autoCorrectActive
    if autoCorrectActive then
        TweenService:Create(Ball, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(50,200,50)}):Play()
        TweenService:Create(ts, TweenInfo.new(0.2), {Color = Color3.fromRGB(50,200,50)}):Play()
        Status.Text = "✔ Auto Correct active!"
        Status.TextColor3 = Color3.fromRGB(100,255,100)
        installHook()
    else
        TweenService:Create(Ball, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(80,80,80)}):Play()
        TweenService:Create(ts, TweenInfo.new(0.2), {Color = Color3.fromRGB(80,80,80)}):Play()
        Status.Text = "Disabled."
        Status.TextColor3 = Color3.fromRGB(150,150,150)
        Result.Text = ""
    end
end)

Main.Size = UDim2.new(0,0,0,0)
Main.Position = UDim2.new(0.5,0,0.5,0)
TweenService:Create(Main, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
    Size = UDim2.new(0,260,0,210),
    Position = UDim2.new(0.5,-130,0.5,-105)
}):Play()
