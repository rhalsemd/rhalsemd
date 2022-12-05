import styled from "@emotion/styled";
import { useEffect, useState } from "react";
import GitHubCalendar from "react-github-calendar";
import ReactTooltip from "react-tooltip";

export default function GithubChart(props: { githubId: string }) {
  // 렌더링 전에 react-tooltip을 불러오지 않게 하기 위해 사용
  const [isMounted, setIsMounted] = useState(false);
  useEffect(() => {
    setIsMounted(true);
  }, []);

  return (
    <>
      <Wrapper>
       {isMounted && (
          <GitHubCalendar
            username={props.githubId}
            labels={{
              totalCount: "Learn how we count contributions",
            }}
            showWeekdayLabels
          >
            <ReactTooltip html />
          </GitHubCalendar>
        )}
      </Wrapper>
    </>
  );
}

const Wrapper = styled.div`
  background-color: white;
  padding: 20px;
`;

const Chart = styled.img`
  width: 855px;
`;
