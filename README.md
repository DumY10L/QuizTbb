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
Main.Size = UDim2.new(0, 260, 0, 0)
Main.Position = UDim2.new(0.5, -130, 0.5, -100)
Main.BackgroundColor3 = Color3.fromRGB(14, 14, 14)
Main.BorderSizePixel = 0
Main.Active = true
Main.Draggable = true
Main.ClipsDescendants = true
Main.Parent = ScreenGui
Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 6)
local MainStroke = Instance.new("UIStroke", Main)
MainStroke.Color = Color3.fromRGB(40, 40, 40)
MainStroke.Thickness = 1.2

local TopBar = Instance.new("Frame", Main)
TopBar.Size = UDim2.new(1, 0, 0, 36)
TopBar.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
TopBar.BorderSizePixel = 0
Instance.new("UICorner", TopBar).CornerRadius = UDim.new(0, 6)

local TopFix = Instance.new("Frame", TopBar)
TopFix.Size = UDim2.new(1, 0, 0, 8)
TopFix.Position = UDim2.new(0, 0, 1, -8)
TopFix.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
TopFix.BorderSizePixel = 0

local DragIcon = Instance.new("TextLabel", TopBar)
DragIcon.Size = UDim2.new(0, 20, 1, 0)
DragIcon.Position = UDim2.new(0, 8, 0, 0)
DragIcon.BackgroundTransparency = 1
DragIcon.Text = "⠿"
DragIcon.TextColor3 = Color3.fromRGB(70, 70, 70)
DragIcon.TextSize = 16
DragIcon.Font = Enum.Font.GothamBold

local Title = Instance.new("TextLabel", TopBar)
Title.Size = UDim2.new(1, -80, 1, 0)
Title.Position = UDim2.new(0, 30, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "Chronos Mathematics"
Title.TextColor3 = Color3.fromRGB(220, 220, 220)
Title.TextSize = 13
Title.Font = Enum.Font.GothamBold
Title.TextXAlignment = Enum.TextXAlignment.Left

local MinBtn = Instance.new("TextButton", TopBar)
MinBtn.Size = UDim2.new(0, 20, 0, 20)
MinBtn.Position = UDim2.new(1, -46, 0.5, -10)
MinBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
MinBtn.Text = "─"
MinBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
MinBtn.TextSize = 10
MinBtn.Font = Enum.Font.GothamBold
MinBtn.BorderSizePixel = 0
Instance.new("UICorner", MinBtn).CornerRadius = UDim.new(0, 4)

local CloseBtn = Instance.new("TextButton", TopBar)
CloseBtn.Size = UDim2.new(0, 20, 0, 20)
CloseBtn.Position = UDim2.new(1, -24, 0.5, -10)
CloseBtn.BackgroundColor3 = Color3.fromRGB(180, 35, 35)
CloseBtn.Text = "✕"
CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseBtn.TextSize = 10
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.BorderSizePixel = 0
Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0, 4)

local Divider = Instance.new("Frame", Main)
Divider.Size = UDim2.new(1, -20, 0, 1)
Divider.Position = UDim2.new(0, 10, 0, 36)
Divider.BackgroundColor3 = Color3.fromRGB(32, 32, 32)
Divider.BorderSizePixel = 0

local Content = Instance.new("Frame", Main)
Content.Size = UDim2.new(1, 0, 1, -37)
Content.Position = UDim2.new(0, 0, 0, 37)
Content.BackgroundTransparency = 1
Content.BorderSizePixel = 0

local ContentPad = Instance.new("UIPadding", Content)
ContentPad.PaddingLeft = UDim.new(0, 12)
ContentPad.PaddingRight = UDim.new(0, 12)
ContentPad.PaddingTop = UDim.new(0, 10)
ContentPad.PaddingBottom = UDim.new(0, 10)

local ContentLayout = Instance.new("UIListLayout", Content)
ContentLayout.SortOrder = Enum.SortOrder.LayoutOrder
ContentLayout.Padding = UDim.new(0, 8)

local SubLabel = Instance.new("TextLabel", Content)
SubLabel.Size = UDim2.new(1, 0, 0, 16)
SubLabel.BackgroundTransparency = 1
SubLabel.Text = "Chapter 4 — Stage 30 · Teapots of Utopia"
SubLabel.TextColor3 = Color3.fromRGB(80, 80, 80)
SubLabel.TextSize = 10
SubLabel.Font = Enum.Font.Gotham
SubLabel.TextXAlignment = Enum.TextXAlignment.Left

local RowQuiz = Instance.new("Frame", Content)
RowQuiz.Size = UDim2.new(1, 0, 0, 38)
RowQuiz.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
RowQuiz.BorderSizePixel = 0
Instance.new("UICorner", RowQuiz).CornerRadius = UDim.new(0, 6)
local RowQuizStroke = Instance.new("UIStroke", RowQuiz)
RowQuizStroke.Color = Color3.fromRGB(38, 38, 38)
RowQuizStroke.Thickness = 1

local RowQuizLabel = Instance.new("TextLabel", RowQuiz)
RowQuizLabel.Size = UDim2.new(1, -80, 1, 0)
RowQuizLabel.Position = UDim2.new(0, 12, 0, 0)
RowQuizLabel.BackgroundTransparency = 1
RowQuizLabel.Text = "Clock Quiz"
RowQuizLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
RowQuizLabel.TextSize = 13
RowQuizLabel.Font = Enum.Font.GothamBold
RowQuizLabel.TextXAlignment = Enum.TextXAlignment.Left

local CallBtn = Instance.new("TextButton", RowQuiz)
CallBtn.Size = UDim2.new(0, 58, 0, 26)
CallBtn.Position = UDim2.new(1, -66, 0.5, -13)
CallBtn.BackgroundColor3 = Color3.fromRGB(200, 160, 0)
CallBtn.Text = "call"
CallBtn.TextColor3 = Color3.fromRGB(15, 15, 15)
CallBtn.TextSize = 12
CallBtn.Font = Enum.Font.GothamBold
CallBtn.BorderSizePixel = 0
Instance.new("UICorner", CallBtn).CornerRadius = UDim.new(0, 5)

CallBtn.MouseEnter:Connect(function()
    TweenService:Create(CallBtn, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(230, 185, 0)}):Play()
end)
CallBtn.MouseLeave:Connect(function()
    TweenService:Create(CallBtn, TweenInfo.new(0.15), {BackgroundColor3 = Color3.fromRGB(200, 160, 0)}):Play()
end)

local Status = Instance.new("TextLabel", Content)
Status.Size = UDim2.new(1, 0, 0, 16)
Status.BackgroundTransparency = 1
Status.Text = ""
Status.TextColor3 = Color3.fromRGB(100, 255, 100)
Status.TextSize = 11
Status.Font = Enum.Font.Gotham
Status.TextXAlignment = Enum.TextXAlignment.Left
Status.TextWrapped = true

local RowAuto = Instance.new("Frame", Content)
RowAuto.Size = UDim2.new(1, 0, 0, 38)
RowAuto.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
RowAuto.BorderSizePixel = 0
Instance.new("UICorner", RowAuto).CornerRadius = UDim.new(0, 6)
local RowAutoStroke = Instance.new("UIStroke", RowAuto)
RowAutoStroke.Color = Color3.fromRGB(38, 38, 38)
RowAutoStroke.Thickness = 1

local AutoLabel = Instance.new("TextLabel", RowAuto)
AutoLabel.Size = UDim2.new(1, -70, 1, 0)
AutoLabel.Position = UDim2.new(0, 12, 0, 0)
AutoLabel.BackgroundTransparency = 1
AutoLabel.Text = "Auto Correct"
AutoLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
AutoLabel.TextSize = 13
AutoLabel.Font = Enum.Font.GothamBold
AutoLabel.TextXAlignment = Enum.TextXAlignment.Left

local SliderBg = Instance.new("Frame", RowAuto)
SliderBg.Size = UDim2.new(0, 44, 0, 22)
SliderBg.Position = UDim2.new(1, -54, 0.5, -11)
SliderBg.BackgroundColor3 = Color3.fromRGB(55, 55, 55)
SliderBg.BorderSizePixel = 0
Instance.new("UICorner", SliderBg).CornerRadius = UDim.new(1, 0)

local SliderDot = Instance.new("Frame", SliderBg)
SliderDot.Size = UDim2.new(0, 18, 0, 18)
SliderDot.Position = UDim2.new(0, 2, 0.5, -9)
SliderDot.BackgroundColor3 = Color3.fromRGB(180, 180, 180)
SliderDot.BorderSizePixel = 0
Instance.new("UICorner", SliderDot).CornerRadius = UDim.new(1, 0)

local SliderBtn = Instance.new("TextButton", SliderBg)
SliderBtn.Size = UDim2.new(1, 0, 1, 0)
SliderBtn.BackgroundTransparency = 1
SliderBtn.Text = ""
SliderBtn.ZIndex = 2

local Result = Instance.new("TextLabel", Content)
Result.Size = UDim2.new(1, 0, 0, 40)
Result.BackgroundTransparency = 1
Result.Text = ""
Result.TextColor3 = Color3.fromRGB(100, 255, 100)
Result.TextSize = 17
Result.Font = Enum.Font.GothamBold
Result.TextXAlignment = Enum.TextXAlignment.Center
Result.TextWrapped = true

-- Notificação canto superior direito
local Notif = Instance.new("Frame", ScreenGui)
Notif.Size = UDim2.new(0, 220, 0, 44)
Notif.Position = UDim2.new(1, 10, 0, 16)
Notif.BackgroundColor3 = Color3.fromRGB(14, 14, 14)
Notif.BorderSizePixel = 0
Notif.ZIndex = 10
Instance.new("UICorner", Notif).CornerRadius = UDim.new(0, 6)
local NotifStroke = Instance.new("UIStroke", Notif)
NotifStroke.Color = Color3.fromRGB(40, 40, 40)
NotifStroke.Thickness = 1.2

local NotifLabel = Instance.new("TextLabel", Notif)
NotifLabel.Size = UDim2.new(1, -16, 1, 0)
NotifLabel.Position = UDim2.new(0, 12, 0, 0)
NotifLabel.BackgroundTransparency = 1
NotifLabel.Text = "Resposta:  —"
NotifLabel.TextColor3 = Color3.fromRGB(100, 255, 100)
NotifLabel.TextSize = 14
NotifLabel.Font = Enum.Font.GothamBold
NotifLabel.TextXAlignment = Enum.TextXAlignment.Left
NotifLabel.ZIndex = 11

local function showNotif(answerName)
    NotifLabel.Text = "Resposta:  " .. answerName
    TweenService:Create(Notif, TweenInfo.new(0.35, Enum.EasingStyle.Quint, Enum.EasingDirection.Out), {
        Position = UDim2.new(1, -230, 0, 16)
    }):Play()
    task.delay(5, function()
        TweenService:Create(Notif, TweenInfo.new(0.35, Enum.EasingStyle.Quint, Enum.EasingDirection.In), {
            Position = UDim2.new(1, 10, 0, 16)
        }):Play()
    end)
end

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
local minimized = false
local fullHeight = 220

local function processQuiz(gui)
    task.spawn(function()
        task.wait(2.5)

        local hourMap = buildImageMap(sprites.Hour)
        local minuteMap = buildImageMap(sprites.Minute)

        local parentFrame = gui.Frame:FindFirstChild("Question") or gui.Frame:FindFirstChild("QuestionTroll")
        if not parentFrame then return end

        local totalMinute = 0
        local firstHour = nil
        local clockCount = 0

        for _, obj in ipairs(parentFrame:GetChildren()) do
            if obj.Name == "Clock" then
                local hourImg = obj:FindFirstChild("Hour")
                local minuteImg = obj:FindFirstChild("Minute")
                if hourImg and minuteImg then
                    local h = hourMap[hourImg.Image]
                    local m = minuteMap[minuteImg.Image]
                    if h ~= nil and m ~= nil then
                        if firstHour == nil then firstHour = h end
                        totalMinute = totalMinute + m
                        clockCount = clockCount + 1
                    end
                end
            end
        end

        if clockCount == 0 then return end

        totalMinute = totalMinute % 12

        local choices = gui.Frame.Choices
        local correctBtn = nil

        for _, btn in ipairs(choices:GetChildren()) do
            if btn:IsA("ImageButton") then
                local btnHour = btn:FindFirstChild("Hour")
                local btnMinute = btn:FindFirstChild("Minute")
                if btnHour and btnMinute then
                    local bh = hourMap[btnHour.Image]
                    local bm = minuteMap[btnMinute.Image]
                    if clockCount == 1 then
                        if bh == firstHour and bm == totalMinute then
                            correctBtn = btn
                            break
                        end
                    else
                        if bm == totalMinute then
                            correctBtn = btn
                            break
                        end
                    end
                end
            end
        end

        if correctBtn then
            if minimized then
                showNotif(correctBtn.Name)
            else
                Status.Text = "✔ Answer found!"
                Status.TextColor3 = Color3.fromRGB(100, 255, 100)
                Result.Text = "👉 " .. correctBtn.Name .. " 👈"
                Result.TextColor3 = Color3.fromRGB(100, 255, 100)
            end
        end
    end)
end

CallBtn.MouseButton1Click:Connect(function()
    local ok, err = pcall(function()
        if playerGui:FindFirstChild("ClockQuiz") then
            playerGui.ClockQuiz:Destroy()
        end
        local clone = game:GetService("ReplicatedStorage").Cutscenes.ClockQuiz:Clone()
        clone.Parent = playerGui
        Status.Text = "✔ Clock Quiz opened!"
        Status.TextColor3 = Color3.fromRGB(100, 255, 100)
        task.delay(2, function()
            Status.Text = ""
        end)
    end)
    if not ok then
        Status.Text = "✘ " .. tostring(err)
        Status.TextColor3 = Color3.fromRGB(255, 80, 80)
    end
end)

local function installHook()
    if hookInstalled then return end
    hookInstalled = true
    playerGui.ChildAdded:Connect(function(gui)
        if gui.Name == "ClockQuiz" and autoCorrectActive then
            if not minimized then
                Status.Text = "Quiz detected!"
                Status.TextColor3 = Color3.fromRGB(255, 255, 0)
                Result.Text = ""
            end
            processQuiz(gui)
        end
    end)
end

SliderBtn.MouseButton1Click:Connect(function()
    autoCorrectActive = not autoCorrectActive
    if autoCorrectActive then
        TweenService:Create(SliderBg, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(30, 90, 220)}):Play()
        TweenService:Create(SliderDot, TweenInfo.new(0.2), {Position = UDim2.new(1, -20, 0.5, -9), BackgroundColor3 = Color3.fromRGB(255, 255, 255)}):Play()
        Status.Text = "✔ Auto Correct active!"
        Status.TextColor3 = Color3.fromRGB(100, 255, 100)
        installHook()
    else
        TweenService:Create(SliderBg, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(55, 55, 55)}):Play()
        TweenService:Create(SliderDot, TweenInfo.new(0.2), {Position = UDim2.new(0, 2, 0.5, -9), BackgroundColor3 = Color3.fromRGB(180, 180, 180)}):Play()
        Status.Text = ""
        Result.Text = ""
    end
end)

CloseBtn.MouseButton1Click:Connect(function()
    TweenService:Create(Main, TweenInfo.new(0.2), {
        Size = UDim2.new(0, 0, 0, 0),
        Position = UDim2.new(0.5, 0, 0.5, 0)
    }):Play()
    task.wait(0.2)
    ScreenGui:Destroy()
end)

MinBtn.MouseButton1Click:Connect(function()
    minimized = not minimized
    if minimized then
        task.delay(0.1, function()
            Content.Visible = false
        end)
        TweenService:Create(Main, TweenInfo.new(0.2), {Size = UDim2.new(0, 260, 0, 36)}):Play()
        MinBtn.Text = "▲"
    else
        Content.Visible = true
        TweenService:Create(Main, TweenInfo.new(0.2), {Size = UDim2.new(0, 260, 0, fullHeight)}):Play()
        MinBtn.Text = "─"
    end
end)

Main.Size = UDim2.new(0, 0, 0, 0)
Main.Position = UDim2.new(0.5, 0, 0.5, 0)
TweenService:Create(Main, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
    Size = UDim2.new(0, 260, 0, fullHeight),
    Position = UDim2.new(0.5, -130, 0.5, -110)
}):Play()
